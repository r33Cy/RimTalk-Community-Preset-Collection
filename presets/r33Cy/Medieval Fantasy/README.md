# Preset Name: Medieval Fantasy
*Created by r33Cy*

## Summary
The **Medieval Fantasy** preset is a high-fidelity "Scene Director" for RimWorld, designed to completely overhaul the game's narrative tone. It interprets real-time game data and converts it into a gritty, low-fantasy dialogue system. By stripping away modern language and industrial terminology, it creates an immersive atmosphere where pawns speak as hardy survivors in a world of steel and hearths.

**Best Used With:** High-immersion "Medieval Overhaul" playthroughs.

## Key Features

* **The Gritty Lexicon (Mandatory Translation):** This preset strictly forbids modern slang (e.g., "okay," "cool," "guys") and industrial or sci-fi terminology. Modern concepts are automatically mapped to medieval equivalents: "Resources" become **"Stores,"** "Experience" becomes **"Bloody Lessons,"** and "Project" becomes **"Toil"** or **"Endeavor"**.
* **Character Archetype Enforcement:** Dialogue is filtered through status-specific roles; for example, Slaves must address colonists as **"Master"** or **"Mistress,"** while colonists address peers as **"kin"** or **"brother/sister"**.
* **Personality-Driven Syntax (The Personality Lock):** The preset utilizes over 25 distinct personality overrides—such as "Stoic," "Abrasive," "Haughty," or "Simpleton"—to dictate the specific rhythm, vocabulary, and grammar of a pawn’s speech.
* **Dynamic Social Mode Logic:** The system intelligently switches between "Solo Mode" (a single thought or soliloquy) and "Social Mode," which mandates a dialogue chain of **4 to 8 turns** to ensure a natural back-and-forth between characters.
* **Anti-"Sage" Mandate:** To keep the setting grounded, the preset prohibits flowery narrator prose and restricts high-medieval grammar (e.g., "thee" and "thou") to characters with high social status or noble backgrounds.
* **Colony & World Awareness:** Integrated with **Event+**, pawns are aware of active threats, map conditions, and ongoing quests, allowing them to discuss the "Perilous" state of the world in real-time.
* **Gender-Locked Kinship:** The AI cross-references the [Gender] field to ensure appropriate terms like "Sir," "Dame," "Brother," or "Sister" are used correctly during interactions.
* **Cognitive Consistency:** Features a strict "Scene Execution Protocol" that ensures the AI stays on topic, avoids repetitive tropes, and uses the History Layer for background continuity only.
* **Advanced Profile Engineering:** The preset uses custom Handlebars logic to clean raw game data, renaming conflicting tags to "Current Mood Modifiers" and stripping technical formatting for a cleaner AI prompt.
* **"Crowded Thought" Trigger:** Implements a specific rule where if a pawn has a "thought" in a social setting, the AI forces them to "mutter aloud" (to self) to allow nearby pawns to hear and react, triggering a social dialogue chain instead of a private moment.
* **Beast Addressing Logic:** Contains specialized protocols for interacting with animals, forcing the AI to use "Instinctive Reaction" language such as frantic commands or guttural curses rather than standard speech.
* **Data Quarantine Protocol:** Strictly forbids the AI from parroting raw text from internal perspectives or chronological events; it forces the generation of entirely new dialogue based on those contexts.
* **The "Void Rule":** Automatically cross-checks the `CanTalk` status from pawn profiles; if a pawn is incapacitated or otherwise ineligible, the system locks the AI into a "None" action.
* **Latin-Only Restriction:** A strict technical guardrail that prevents CJK (Chinese, Japanese, Korean) characters or Unicode symbols from bleeding into the output, ensuring compatibility with English-only interfaces.
* **Double-Translation Engine:** Acts as a bridge for players using multi-language mod setups by interpreting Chinese intent-parsing data and translating it first to English, then to the "Gritty Medieval" dialect.

---

## Required Add-On Mods
* [RimTalk](https://steamcommunity.com/sharedfiles/filedetails/?id=3551203752) (Main Framework)
* [RimTalk Event+](https://steamcommunity.com/sharedfiles/filedetails/?id=3612632140) (For quest, threat and map condition awareness)
* [RimTalk - Expand Memory](https://steamcommunity.com/sharedfiles/filedetails/?id=3608181242) (For conversational continuity)
* [RimTalk - Expand Thoughts](https://steamcommunity.com/sharedfiles/filedetails/?id=3661175034) (For psychological depth)

## Recommended Add-On Mods
*These mods aren't required, but they greatly enhance the experience of this preset.*
* [RimTalk: Expand Literature](https://steamcommunity.com/sharedfiles/filedetails/?id=3633249209)  (Converts the subjective thoughts recorded by *Expand Thoughts* into tangible opinion changes in the social panel)
* [RimTalk: Expand Relation](https://steamcommunity.com/sharedfiles/filedetails/?id=3661493651) (To track opinion changes; Trust, affection, and respect automatically influence social standings with gradual, smooth changes that track thought decay)
* [RimTalk DynamicColors](https://steamcommunity.com/sharedfiles/filedetails/?id=3628773219) (For visual highlighting for names and keywords, making dialogue easier to follow)

---

## Preset Notes
*These are not necessary for the preset to function but my current settings that work well for me.*

### AI Model & Provider
* **Model:** DeepSeek-R1-Distill-Qwen-32B-GGUF
* **Provider/API:** LlamaCpp (Local)

The listed model is an example that works well with this preset but requires high-end hardware for local inference (preferably a GPU with at least **32 GB of VRAM** if running both the model and game on the same system). Users are free to choose any model and should select a size that matches their available VRAM to ensure smooth performance.

### AI Settings Tips
* **Logic & Creativity:**
    * **Temperature:** `0.78` — Controls randomness; higher values make medieval prose more creative and flowery. Don't go above `0.85`.
    * **Min-P:** `0.03` — Strips away low-probability "nonsense" tokens while keeping the vocabulary diverse.
    * **Top-P:** `1.0` — Limits the cumulative probability of word choices to ensure consistent logic. A setting of `1.0` equals disabled. We are letting `Min-P`, the better filter, do the work.
    * **Top-K:** `50` — Restricts the model to selecting from the 50 most likely next words. At higher temperatures (above `0.72`), this acts as a safeguard.
* **Repetition Control:**
    * **Repeat Penalty:** `1.05` — Discourages the AI from using the exact same word too frequently in a short window.
    * **Repeat Last N:** `4096` — The token range the AI scans to identify and penalize repeated words.
* **DRY Sampler (The "Nuclear" Fix):**
    * **Dry Mult:** `0.5` — The strength of the DRY penalty; keeps the AI from repeating medieval tropes too often.
    * **Dry Base:** `1.75` — The exponential factor for the penalty, making repetitive phrases increasingly unlikely.
    * **Dry Allowed Len:** `10` — Allows short, common medieval phrases (up to 10 characters) to be reused without penalty.
    * **Dry Penalty Last N:** `4096` — Controls how far back the DRY sampler looks to identify repetitive patterns.
* **DeepSeek Reasoning Format:**
    * **Format:** `deepseek` — Critical setting. Allows the model to extract thoughts into a hidden field so the game only receives clean dialogue.
* **Context Length:** `24576` (24k) — Essential for handling the heavy data overhead from the **Expand** mod series.

### Other Details
Due to the complexity of the "Personality Lock" and the "Gritty Lexicon," this preset is best paired with **Reasoning Models** (like DeepSeek-R1 or similar) that can handle the complex "Scene Execution Protocol" without breaking character.