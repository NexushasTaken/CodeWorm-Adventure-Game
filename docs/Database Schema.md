```postgresql
-- Core Tables (Minimal Changes)
CREATE TABLE concepts (
    id SERIAL PRIMARY KEY,
    name TEXT NOT NULL UNIQUE,
    description TEXT,
);

CREATE TABLE scenarios (
    id SERIAL PRIMARY KEY,
    concept_id INTEGER NOT NULL REFERENCES concepts(id),
    name TEXT NOT NULL,
    UNIQUE(concept_id, name)
);

-- Player Progress (Optimized)
CREATE TABLE player_scenario_runs (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    user_id UUID NOT NULL REFERENCES auth.users(id),
    scenario_id INTEGER NOT NULL REFERENCES scenarios(id),
    -- Metrics
    speed_seconds FLOAT NOT NULL,
    accuracy_score INTEGER NOT NULL,
    efficiency_score FLOAT NOT NULL,
    -- Progress
    is_first_completion BOOLEAN NOT NULL DEFAULT FALSE,
    completion_count INTEGER NOT NULL DEFAULT 1,
    -- Timestamps
    completed_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
);

CREATE TABLE player_concept_progress (
    user_id UUID NOT NULL REFERENCES auth.users(id),
    concept_id INTEGER NOT NULL REFERENCES concepts(id),
    is_unlocked BOOLEAN NOT NULL DEFAULT FALSE,
    unlocked_at TIMESTAMPTZ NOT NULL DEFAULT NOW(),
    PRIMARY KEY (user_id, concept_id)
);

-- Saves
CREATE TABLE player_scenario_saves (
    user_id UUID NOT NULL REFERENCES auth.users(id),
    scenario_id INTEGER NOT NULL REFERENCES scenarios(id),
    tile_data JSONB NOT NULL,
    updated_at TIMESTAMPTZ NOT NULL DEFAULT NOW(),
    PRIMARY KEY (user_id, scenario_id)
);

-- Leaderboards
CREATE TABLE scenario_records (
    scenario_id INTEGER NOT NULL REFERENCES scenarios(id),
    record_type TEXT NOT NULL CHECK (record_type IN ('speed', 'accuracy', 'efficiency')),
    record_value FLOAT NOT NULL,
    updated_at TIMESTAMPTZ NOT NULL DEFAULT NOW(),
    PRIMARY KEY (scenario_id, record_type)
);

-- Cosmetics (Fixed References)
CREATE TABLE skins (
    id TEXT PRIMARY KEY,
    display_name TEXT NOT NULL,
    is_default BOOLEAN NOT NULL DEFAULT FALSE
);

CREATE TABLE player_skins (
    user_id UUID NOT NULL REFERENCES auth.users(id),
    skin_id TEXT NOT NULL REFERENCES skins(id),
    unlocked_at TIMESTAMPTZ NOT NULL DEFAULT NOW(),
    PRIMARY KEY (user_id, skin_id)
);

CREATE TABLE player_selected_skin (
    user_id UUID PRIMARY KEY REFERENCES auth.users(id),
    skin_id TEXT NOT NULL REFERENCES skins(id),
    selected_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
);

-- Achievements (Unchanged)
CREATE TABLE achievements (
    id TEXT PRIMARY KEY,
    name TEXT NOT NULL,
    description TEXT NOT NULL
);

CREATE TABLE player_achievements (
    user_id UUID NOT NULL REFERENCES auth.users(id),
    achievement_id TEXT NOT NULL REFERENCES achievements(id),
    unlocked_at TIMESTAMPTZ NOT NULL DEFAULT NOW(),
    PRIMARY KEY (user_id, achievement_id)
);
```