# Information Extraction Prompts

Alright, as a smart Analytic Agent and Prompt designer, I'm ready to craft some truly novel and detailed prompts for information extraction. My goal is to push beyond typical document parsing and imagine scenarios where the 'information' is hidden, contextual, or requires intricate logical deduction.

---

### **Prompt 1: Deconstructing "Lost Futures" from Obsolete Patents**

**Concept:** Extracting detailed technological concepts, societal aspirations, and unforeseen limitations from collections of unfulfilled or obsolete patent applications.

**The Prompt:**

>"Imagine you have access to a vast, digitized archive of **obsolete or ungranted patent applications** spanning the last two centuries (e.g., from the late 1800s to the early 2000s). These aren't patents for successful inventions, but for ideas that never materialized, were technically unfeasible at the time, or were simply too eccentric to gain traction. Your task is to perform an advanced information extraction to reveal the 'lost futures' envisioned by past inventors.

**Your goal is to extract the following information, focusing on patterns and thematic insights:**

1.  **Core Invention Concept:** For each patent, a concise summary (1-2 sentences) of the primary technological breakthrough or solution it proposed.
2.  **Intended Societal Problem/Benefit:** What specific societal issue or human need was this invention trying to address? (e.g., 'faster travel', 'household automation', 'new energy source', 'disease cure'). Categorize these into broader themes.
3.  **Predicted Impact/Future Vision:** What explicit or implicit future (technological, social, economic) did the inventor envision if their patent succeeded? Look for keywords related to lifestyle changes, industrial shifts, or utopian/dystopian outcomes.
4.  **Assumed Technological Prerequisites:** What existing or soon-to-be-available technologies did the inventor implicitly rely on for their invention to work? (e.g., 'cheap electricity', 'advanced metallurgy', 'miniaturized components').
5.  **Unforeseen Limitations/Obstacles:** Based on our current understanding, identify why the patent likely failed or remained unfulfilled. Look for mentions of materials, energy, data processing capabilities, or social acceptance that were lacking at the time.
6.  **Cross-Temporal Design Patterns:** Identify instances where similar conceptual problems or proposed solutions re-emerge across different decades, perhaps with updated technological approaches.

**Constraint:** The extraction should not just pull direct text. It must involve **semantic understanding and inferencing** to connect the proposed solution to its broader societal context and the inventor's underlying worldview. For example, if a patent describes 'self-driving carriages for all', you should infer 'autonomous transportation for societal equity' as a predicted impact.

**Output:** A structured dataset (e.g., JSON or CSV) where each row represents a patent, with columns for the extracted fields. Additionally, generate a thematic summary outlining the prevalent 'lost futures' and the most common reasons for their unfulfillment across the analyzed period."


---
### **Prompt 2: De-Ciphering Narrative Intent from Micro-Expressions in Unscripted Interviews**

**Concept:** Extracting underlying emotional narratives and concealed information from subtle, non-verbal cues in transcribed unscripted interviews.

**The Prompt:**

>"You are presented with a series of **transcribed, unscripted interview segments** (text format only, no audio/video) from individuals discussing a past, complex event (e.g., a corporate merger, a community dispute, a natural disaster response). While the spoken words provide explicit information, your primary task is to extract the **implicit emotional narratives, hidden tensions, and potentially concealed information** by analyzing patterns of hesitation, emphasis, repetition, self-correction, and the *implied context* of their micro-expressions.

**Your goal is to extract the following information for each interviewee, for each segment:**

1.  **Dominant Emotional State (Inferred):** Identify the primary underlying emotion conveyed (e.g., 'anxiety', 'defensiveness', 'excitement', 'resignation', 'sarcasm', 'genuine relief') that might contradict or subtly alter the meaning of their explicit statements. Provide a confidence score for this inference.
2.  **Points of Hesitation/Uncertainty:** Pinpoint specific phrases or topics where the interviewee shows signs of verbal hesitation (e.g., 'um', 'uh', prolonged pauses, stuttering, repeated words) and infer the *reason* for this hesitation (e.g., 'struggling to recall', 'deliberate obfuscation', 'emotional discomfort').
3.  **Emphasis/Significance (Implied):** Identify words or phrases that carry a heavier unspoken weight or significance, even if not explicitly stated as important. This could be due to unusual word choice, placement in a sentence, or implied emphasis.
4.  **Narrative Discrepancies/Inconsistencies:** Cross-reference an interviewee's statements within the same segment or across different segments to identify subtle contradictions or evasions that suggest incomplete or manipulated information.
5.  **Unstated Relationships/Power Dynamics:** Infer the interviewee's perceived relationship or power dynamic with other mentioned individuals or entities based on their language, emotional tone, and phrasing, even if never explicitly stated.
6.  **Concealed Information Hypothesis:** Formulate a concise hypothesis (1-2 sentences) about any specific piece of information or context that the interviewee might be intentionally withholding or downplaying.

**Constraint:** You *cannot* rely on explicit statements like 'I felt nervous'. Instead, focus on the *how* they say things through textual cues. This requires advanced **natural language understanding, sentiment analysis, and pattern recognition** that goes beyond simple keyword spotting.

**Output:** A detailed report (JSON or markdown) for each interview segment, listing the extracted insights for each field. Include a summary section identifying the most significant areas of tension or potential concealment across the entire interview set."

---

### **Prompt 3: Mapping the Unseen "Flows" in Urban Decay Documentation**

**Concept:** Extracting and mapping the invisible networks and processes (e.g., waste dispersal, water seepage, rodent migration, illicit activity routes) from observational reports and photographic metadata of urban decay.

**The Prompt:**

>"You are tasked with analyzing a rich dataset documenting urban decay in a specific abandoned district. This dataset includes:
* **Architectural blueprints and structural integrity reports** (PDF/text).
* **Photographic metadata** from drone and ground-level imagery (EXIF data, geotags, timestamps, object detection tags for things like 'puddles', 'rust patterns', 'vandalism', 'discarded waste').
* **Ethnographic notes** from urban explorers describing sensory experiences ('damp smell', 'scuttling sounds', 'graffiti patterns', 'traces of makeshift shelters').
* **Historical local weather data** (temperature, precipitation).

Your objective is not just to describe the decay, but to extract and map the **"unseen flows"** within this environment – the dynamic, often hidden processes that contribute to and are sustained by the decay.

**Your goal is to extract the following information, integrating across data types:**

1.  **Water Infiltration & Drainage Paths:** Identify main points of water entry (leaky roofs, burst pipes), internal flow routes (stairwells, elevator shafts, cracks), and pooling areas. Infer potential underground or hidden drainage channels.
2.  **Waste Accumulation & Dispersal Vectors:** Map areas of significant waste buildup. Infer the likely entry points of waste, its primary dispersal mechanisms (wind, rodents, human activity), and the destinations of this dispersal within the district.
3.  **Biodeterioration Spread:** Track the likely propagation paths of mold, mildew, invasive plant species, and insect/rodent infestations. Connect observations of damage types to probable biological agents.
4.  **Human Usage Patterns (Illicit/Informal):** Identify inferred pathways, recurring gathering spots, and evidence of temporary habitation or specific activities (e.g., drug use, shelter-seeking, artistic expression) based on discarded items, wear patterns, and graffiti.
5.  **Environmental Micro-climates:** Infer localized pockets of extreme temperature, humidity, or air stagnation based on material degradation patterns, condensation, and plant growth, correlating with external weather data.
6.  **Structural Failure Propagation:** Based on reports and visual cues, map how initial structural failures (e.g., a cracked wall) propagate stress and contribute to subsequent failures across connected parts of a building or even adjacent structures.

**Constraint:** The information for these 'flows' is rarely explicit. You must use **multi-modal data fusion and causal inferencing** to connect disparate observations (e.g., a specific type of mold in photos + high humidity readings + a leaky pipe in blueprints = a probable water flow path).

**Output:** A geo-referenced dataset (e.g., GeoJSON or similar format compatible with mapping software) containing identified 'flow paths' and 'hotspots' for each category, along with a textual explanation of the evidence and inference process for key examples. A summary report highlighting the most dominant unseen flows and their interdependencies."

---

### **Prompt 4: Inferring Socio-Economic Undercurrents from Online Classifieds (Historical Snapshot)**

**Concept:** Extracting latent socio-economic trends, resource scarcity, and community values from a large, historical dataset of online classified advertisements (e.g., Craigslist archives from a specific region over a decade).

**The Prompt:**

>"You have access to an archived dataset of **all classified advertisements** posted in a major metropolitan area's online forum (like Craigslist) for a continuous period of 10 years (e.g., 2005-2015). This includes 'for sale', 'wanted', 'housing', 'jobs', 'services', and 'community' sections. Your task is to go beyond simple keyword counting and extract nuanced information about the **socio-economic undercurrents, shifting values, and resource availability** within that community over time.

**Your goal is to extract the following information, focusing on temporal trends and implicit meanings:**

1.  **Emerging/Declining Industries/Skills:** Identify the rise and fall of specific job types, required skills, or services offered/demanded, correlating with economic shifts (e.g., a surge in 'gig economy' jobs, decline in manufacturing roles).
2.  **Resource Scarcity/Abundance:** Infer periods of scarcity or abundance for specific goods (e.g., 'toilet paper' during a particular event, 'housing shortages' indicated by bidding wars or inflated rent prices, 'free electronics' indicating oversupply).
3.  **Community Values & Concerns:** Detect shifts in what the community values (e.g., 'sustainability' increasing in 'free' or 'wanted' sections, 'safety' concerns in housing ads, 'localism' emphasized in services). Look for implicit social commentary.
4.  **Micro-Economic Indicators:** Identify subtle indicators of economic health or distress, such as the prevalence of 'barter/trade' offers, 'everything must go' sales, or an increase in ads seeking very low-cost or free items.
5.  **Demographic Inferences:** Although not explicitly stated, infer potential changes in demographics (e.g., influx of families indicated by 'childcare wanted' or 'cribs for sale', aging population by 'mobility aid' ads) based on demand/supply patterns.
6.  **Technological Adoption Trajectories:** Track the emergence and mainstream adoption of new technologies (e.g., 'smartphones' appearing as desired items, 'streaming services' mentioned in job ads for internet technicians).

**Constraint:** The ads are often informal, colloquial, and contain abbreviations. The extraction requires sophisticated **contextual analysis, entity recognition, and temporal pattern detection** to identify subtle signals rather than just overt statements. For example, 'ISO vintage vinyl' combined with a decline in 'CD player for sale' might indicate a shift in music consumption habits.

**Output:** A time-series dataset (e.g., CSV or database tables) detailing the extracted trends and their confidence scores, segmented by year or quarter. A narrative report highlighting the most significant socio-economic insights gained from analyzing these classifieds, with supporting examples from the ad text."

---

### **Prompt 5: Unearthing "Silent Protocols" from Archived Scientific Correspondence**

**Concept:** Extracting unwritten laboratory practices, unspoken assumptions, and informal knowledge transfer protocols from a collection of archived, informal scientific correspondence (emails, lab notebooks, handwritten notes).

**The Prompt:**

>"You are presented with a digitized archive of **informal scientific correspondence** (emails, handwritten lab notes, meeting minutes, shared document comments, personal memos) from a specific research group or institution during a pivotal period of discovery (e.g., the development of a new vaccine, a groundbreaking physics experiment, a major archaeological excavation). This data is messy, conversational, and often contains jargon. Your task is to extract the **'silent protocols'**: the unwritten rules, tacit knowledge, informal decision-making processes, and unspoken assumptions that shaped their research but were never formally documented in published papers or official protocols.

**Your goal is to extract the following information, focusing on implicit knowledge:**

1.  **Informal Methodological Adjustments:** Identify instances where researchers discuss ad-hoc changes to experimental procedures, optimizations not mentioned in formal methods sections, or specific 'tricks of the trade' for equipment handling.
2.  **Tacit Knowledge Transfer:** Pinpoint communications where one researcher implicitly or explicitly transfers undocumented skills, intuitive insights, or 'gut feelings' about experimental outcomes to another (e.g., 'you just know when the solution looks right', 'it works best if you do X very slowly').
3.  **Decision-Making Rationales (Beyond Data):** Uncover the unstated reasons behind crucial research decisions that extend beyond direct experimental results (e.g., 'we picked this approach because Dr. Smith always trusts that supplier', 'we avoided that avenue due to a hunch about its stability').
4.  **Implicit Assumptions about Data/Theory:** Identify underlying assumptions about the data's quality, the validity of a theoretical model, or the behavior of reagents/materials that are not explicitly stated as hypotheses but are evident in the discourse.
5.  **Informal Troubleshooting & Problem-Solving:** Extract descriptions of how unexpected experimental failures or equipment malfunctions were *actually* resolved, often through trial-and-error, external consultation, or non-standard approaches.
6.  **Interpersonal Dynamics & Influence:** Infer the unspoken hierarchy, power dynamics, or personal biases within the research group that subtly influenced scientific direction or interpretation of results.

**Constraint:** This requires extremely sophisticated **contextual NLP, discourse analysis, and an understanding of scientific reasoning** to identify nuances in language, tone, and conversational flow that reveal hidden practices. You're looking for what's *implied* or *assumed*, not just what's explicitly stated.

**Output:** A structured knowledge graph or a relational database of 'silent protocols', linking them to specific researchers, dates, and the pieces of correspondence where they were inferred. Include a detailed report outlining the most significant 'silent protocols' discovered, how they were identified, and their likely impact on the research outcomes. This will be invaluable for understanding the true history of scientific discovery."

---
### **Prompt 6: "Narrative Data Sculptor"**
**Use Case** : Extract structured data from personal stories, case studies, or testimonials.

>You are a Narrative Data Sculptor. Given a personal story or anecdote, extract structured insights such as:
- Stakeholders involved (with roles)
- Chronology of events (timestamped if possible)
- Emotional tone per paragraph
- Key decision points and consequences
- Mentioned tools, platforms, or products

**Input**: "{{TEXT}}"

**Output:** JSON with these keys:
```json
{
  "stakeholders": [{"name": "", "role": "", "intent": ""}],
  "timeline": [{"event": "", "timestamp": "", "impact": ""}],
  "emotions_by_section": [{"section": 1, "tone": ""}],
  "decisions": [{"choice": "", "reasoning": "", "outcome": ""}],
  "tools_or_products": ["", ""]
}
```

---

### **Prompt 7: "Policy Decoder & Clause Extractor"**
**Use Case**: Extract critical clauses, exceptions, and conditions from dense legal or policy documents.

>You are a Policy Decoder. Given a policy document or terms & conditions, extract the following:
- Clause Title
- Clause Type (e.g. liability, termination, data usage)
- Conditions/Triggers
- Exceptions/Exemptions
- Enforcement details
- Critical Risks

**Input**: "{{POLICY_TEXT}}"

**Output:** As a structured table or JSON array of clause summaries.

---

### **Prompt 8: "Scientific Fact Miner"**
**Use Case**: Extract discrete factual claims, methods, and quantified results from research papers or academic abstracts.

>You are a Scientific Fact Miner. From the **Input** scientific abstract or section, extract:
- Research Question
- Methodology Summary
- Sample Size & Type
- Key Findings (with numeric data if available)
- Stated Limitations
- Named Entities (institutions, compounds, devices, models)

**Input**: "{{RESEARCH_TEXT}}"

**Output format:** Structured JSON or markdown bullet list for each field.

---

### **Prompt 9: "Threat Intelligence Extractor (CyberSec Edition)"**
**Use Case**: From cybersecurity incident reports or threat feeds, extract structured threat intelligence.

>You are a Cybersecurity Threat Extractor. From the text, extract:
- Threat Actor (name, alias, known groups)
- Attack Vector (e.g. phishing, malware type)
- Indicators of Compromise (IoCs) – IPs, hashes, URLs
- Affected Assets or Systems
- Tactics, Techniques, and Procedures (TTPs) aligned to MITRE ATT&CK
- Mitigation or Response Steps

**Input**: "{{THREAT_REPORT}}"

**Output format:** JSON object categorized by type of intelligence.

---

### **Prompt #5: "Customer Intent Signal Extractor (E-commerce Feedback)"**
**Use Case**: Extract buyer intents, blockers, and conversion clues from product reviews or chat logs.

>You are a Customer Intent Signal Extractor. From customer reviews or pre-purchase chats, extract:
- Stated purchase intent (High, Medium, Low)
- Specific likes/dislikes
- Product features mentioned
- Purchase blockers (e.g., price, availability, trust)
- Sentiment per sentence
- Competitors referenced (if any)

**Input**: "{{CUSTOMER_FEEDBACK}}"

**Output:** Structured table or JSON array by reviewer or message.
