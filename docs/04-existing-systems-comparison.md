
# Existing Systems Comparison

## 1. Purpose and Scope

This document compares five existing systems that address parts of the problem CareerLens targets: helping students and early-career professionals understand what a target role requires, see where their skills fall short, and decide what to learn next. The comparison supports two project objectives: reviewing existing career-development and skill-assessment systems, and justifying the functionality proposed for CareerLens.

The comparison is based on publicly available product documentation, help pages, vendor announcements, and a small number of secondary sources. The systems were not tested hands-on for this version of the document (see Section 9). Ratings therefore describe what the reviewed sources state or do not state, not the full behaviour of each product.

## 2. Selected Systems

The systems were chosen to cover several kinds of tools relevant to career and skill planning. They are not direct copies of the CareerLens concept; each covers a different part of it. Because product features and availability change, the comparison distinguishes publicly documented individual features from organization-oriented offerings.

| System | Type | Why it is included |
|---|---|---|
| O\*NET OnLine | Public occupational information database | A standard source of role requirements, also used as a reference in the literature review |
| LinkedIn Career Explorer | Career-transition tool based on skills similarity | Maps a person's skills to other jobs and suggests skills to add |
| Coursera (role-based recommendations, LevelSets, Skill Tracks) | Online learning platform | Links roles, skills, and learning content; offers skill assessments |
| roadmap.sh | Community-maintained developer roadmaps and paid learning tools | Role-based learning roadmaps, progress tracking, and optional paid features |
| Pluralsight Skill IQ and Role IQ | Technical skill assessment and learning platform | Assessment-based skill gaps with learning recommendations |

## 3. Comparison Criteria

Nine criteria were defined from the CareerLens workflow (select a role, assess skills, find gaps, plan learning, track progress) and from the findings of the literature review, in particular the limits of self-assessment (Zell & Krizan, 2014) and the need for transparent, explainable matching.

| ID | Criterion | Question |
|---|---|---|
| K1 | Role-specific skill requirements | Does the system describe the skills required for a specific role? |
| K2 | Personalized skill gap identification | Does it compare the user's skills with a target role and show what is missing? |
| K3 | Skill verification beyond self-rating | Does it test or otherwise verify skills instead of relying only on what the user claims? |
| K4 | Ordered or prioritized learning guidance | Does it tell the user what to learn first and next? |
| K5 | Skill structure | Does it represent relationships or progression between skills or topics? |
| K6 | Progress tracking and reassessment | Can the user record progress or repeat an assessment to see change? |
| K7 | Transparency of method | Is it explained how scores, matches, or recommendations are produced? |
| K8 | Fit for students and early-career users | Is the system suitable for students and early-career users? |
| K9 | Access and cost transparency | Is access free, paid, or dependent on an organizational subscription, according to the reviewed sources? |

## 4. Rating Scale

- **Yes**: the reviewed sources state that the feature exists.
- **Partial**: the feature exists in a limited form, only for some users (for example, organizations), or only for some skills.
- **No**: the reviewed sources state that the feature is absent or has been withdrawn.
- **Not evidenced**: the reviewed sources do not mention the feature. This is not proof that it is absent.

Source identifiers in square brackets refer to the list in Section 10.

## 5. System Descriptions

### 5.1 O\*NET OnLine

O\*NET OnLine provides detailed descriptions of occupations, with requirements, worker characteristics, and training information for more than 900 occupations [O1]. Each skill or knowledge descriptor is rated on scales such as Importance (1–5) and Level (0–7), and the site documents how these ratings are standardized to a 0–100 range [O1]. Users can search for occupations by skills they select and browse related occupations [O2].

O\*NET is a reference source for role requirements rather than a personal assessment tool. The reviewed sources do not show a function that compares a user's skill levels with an occupation's requirements and reports the gaps.

### 5.2 LinkedIn Career Explorer

LinkedIn Career Explorer was introduced in 2020 to help people find roles they could move into by mapping their skills to job titles. It draws on LinkedIn's skills data (reported as over 36,000 skills and 6,000 job titles) [L4], ranks skills by their importance for a role, and shows skills a person would need to build for a target role [L5]. It also points to relevant LinkedIn Learning courses [L6]. LinkedIn describes a skills-similarity score that reflects both the overlap of skills between two jobs and the relative importance of those skills [L4]. Separately, LinkedIn's job pages show how many of a job's required skills match a member's profile [L2].

LinkedIn discontinued its Skill Assessments, and badges from completed assessments were to be removed from profiles in 2024; the company states that examples of how a candidate applied a skill are more useful to hirers [L1]. A Microsoft support page from 2023 still lists Career Explorer as a free tool [L3]. The descriptions of Career Explorer in the reviewed sources date from 2020 to 2023, and its availability and current behaviour in October 2026 were not confirmed.

### 5.3 Coursera

Coursera provides learner-facing career recommendations that connect a learner's career goals with relevant learning content. Its career guidance materials describe recommendations based on how closely courses teach skills considered important for a role [C1]. Coursera also offers Coursera Coach, an AI-powered assistant, as part of its learning experience [C1].

Coursera's organizational offerings include LevelSets, which are described as skill assessments for establishing learners' current skill levels and identifying strengths and gaps [C2]. Coursera also announced Skill Tracks in September 2025, describing role- and experience-level-based skill and course pathways [C3]. Coursera's Skills Graph is described as connecting skills, learning content, careers, and learners [C4]. These capabilities should not be treated as universally available to every individual learner: the reviewed documentation distinguishes learner-facing recommendations from organizational assessment products. This comparison does not assume that features described as planned in an earlier announcement are currently available unless confirmed by current documentation.

The reviewed sources do not establish that all individual learners receive an explicit skill gap report comparing their assessed proficiency with the requirements of a target role.

### 5.4 roadmap.sh

roadmap.sh is a community-driven platform of role-based and skill-based learning roadmaps for developers. Roadmaps are created and reviewed by the community and subject-matter experts, and users can track their progress as they follow a roadmap [R1]. Each roadmap is divided into topics with explanations and resources, and is designed to show what to study and in what order [R3]. The repository also contains question sets for testing knowledge in some areas [R3]. An AI roadmap generator can produce a roadmap for a topic entered by the user [R2]. Core community roadmaps are publicly accessible, while roadmap.sh also offers paid AI features and paid team plans [R4] [R5].

roadmap.sh does not measure the user's current skills against the roadmap in the reviewed sources: the user decides what they already know.

### 5.5 Pluralsight Skill IQ and Role IQ

Pluralsight provides assessments and learning recommendations focused primarily on technology skills. Its February 2026 help documentation describes Skill IQ assessments as comparative measures that help learners identify a starting point, view their skill levels, and find learning recommendations for specific gaps [P1] [P2]. In October 2026, Pluralsight announced a revised Skill IQ product family, including Skill IQ Discovery (formerly Skill IQ) and Skill IQ Verified, an objective, standards-based assessment with a Pass/Not Passed result [P5]. Because this product change is recent, older help pages may still use the previous Skill IQ naming. Role IQ measures proficiency across the skills associated with a selected technical role and recommends learning opportunities to address gaps; users can retake related assessments to measure progress [P3]. Pluralsight promotes both individual learning and organization/team use. The exact features available can depend on the assessment and plan [P1] [P3] [P5].

## 6. Comparison Table

| Criterion | O\*NET OnLine | LinkedIn Career Explorer | Coursera | roadmap.sh | Pluralsight Skill IQ / Role IQ |
|---|---|---|---|---|---|
| K1 Role-specific requirements | **Yes**: occupation descriptors with Importance and Level ratings [O1] | **Partial**: skills mapped to job titles and ranked by importance [L4] [L5] | **Yes**: role-based recommendations linked to critical skills [C1] | **Yes**: role-based roadmaps [R1] | **Yes**: Role IQ measures skills associated with technical roles [P3] |
| K2 Personalized skill gap | **No**: supports occupation exploration but no personal gap report is evidenced [O2] | **Partial**: suggests skills to develop for a target role; proficiency-level comparison is not evidenced [L5] [L6] | **Partial**: LevelSets identify gaps in organizational settings [C2]; individual role recommendations are not the same as a verified gap report [C1] | **Not evidenced** for individual role-to-proficiency comparison [R1] | **Yes**: reports skill/role gaps and recommends learning [P1] [P3] |
| K3 Skill verification | **Not evidenced** | **No**: LinkedIn states Skill Assessments are no longer available [L1] | **Partial**: LevelSets provide assessments in organizational offerings [C2] | **Partial**: some question sets are available, but role-level verification is not evidenced [R3] | **Yes**: Skill IQ assessments; Role IQ combines role-related assessments [P1] [P3] |
| K4 Ordered or prioritized guidance | **Not evidenced** | **Partial**: links to LinkedIn Learning content; an ordered plan is not evidenced [L6] | **Partial**: role-based recommendations rank relevant learning content [C1] | **Yes**: roadmaps organize topics and resources into a learning sequence [R1] | **Yes**: recommendations guide learners toward areas to improve [P1] |
| K5 Skill structure | **Partial**: occupations and descriptors are structured, but a learning dependency map is not evidenced [O1] | **Not evidenced** in the reviewed sources | **Partial**: Skills Graph connects skills, content, and careers [C4] | **Partial**: visual topic structure; formal prerequisite rules are not evidenced [R1] | **Partial**: role profiles and learning paths organize related skills [P3] |
| K6 Progress tracking and reassessment | **Not evidenced** | **Not evidenced** | **Not evidenced** for individual role-gap progress tracking in the reviewed sources | **Yes**: users can track progress through roadmaps [R1] | **Yes**: users can revisit assessments and learning recommendations; exact rules may vary [P1] |
| K7 Transparency of method | **Yes**: scales and standardized scores are documented [O1] | **Partial**: a skills-similarity concept is described, but the full method is not public in the reviewed sources [L4] | **Partial**: the Skills Graph is described, but the complete recommendation logic is not detailed [C4] | **Partial**: roadmap content is community-curated; individualized matching logic is not evidenced [R1] | **Partial**: comparative assessment is described; full scoring details are not public in the reviewed pages [P1] [P2] |
| K8 Fit for students and early-career users | **Yes**: public occupational information usable by a broad audience [O1] | **Partial**: described for job seekers and career changers; current standalone Career Explorer availability was not confirmed [L3] [L6] | **Yes**: individual learners can use learner-facing recommendations; assessment availability differs by offering [C1] [C2] | **Partial**: useful for self-directed developers, but focused on technology learning [R1] | **Partial**: individual Skill IQ access exists, but Role IQ and team features are also oriented toward organizations [P1] [P3] |
| K9 Access and cost transparency | **Yes**: public resource [O1] | **Not confirmed** for the current standalone Career Explorer experience | **Not assessed**; access may differ between learner and organizational offerings | **Partial**: core roadmaps are publicly accessible, while some learning packs and team features are paid [R1] [R5] | **Partial**: assessment access is available to account holders, while learning content and advanced features depend on plan [P1] [P4] |

## 7. Analysis

**No reviewed system is evidenced to cover the full CareerLens workflow for individual students.** Across the five systems, role information, skill assessment, learning guidance, and progress tracking exist in different combinations. The reviewed sources do not establish that one system consistently combines a documented target-role profile, individual proficiency-based gap analysis, verification beyond self-rating, an ordered learning roadmap, reassessment, and transparent access for students.

**Pluralsight is one of the closest functional matches, particularly for technical skills.** Its Skill IQ assessments identify topic-level strengths and gaps and recommend learning content, while Role IQ assesses skills associated with a role [P1] [P2] [P3]. In October 2026, Pluralsight announced Skill IQ Verified, which it describes as an objective, standards-based assessment, alongside Skill IQ Discovery, the comparative assessment previously called Skill IQ [P5]. However, the platform remains focused primarily on technology skills, and its role and team features also support organizational use. Its assessments and role profiles are not the same as a transparent comparison against a public, independently documented occupational profile; the full scoring and role-mapping details are not all described in the reviewed pages.

**roadmap.sh provides roadmaps and progress tracking, but individual proficiency-based gap analysis is not evidenced in the reviewed sources.** Its official About page describes role- and skill-based roadmaps, learning resources, and progress tracking [R1]. The platform is focused primarily on developer and technology learning. Its separate team offering advertises skill-gap analysis, but that should not be conflated with the individual roadmap experience [R5].

**O\*NET OnLine and LinkedIn Career Explorer support exploration rather than gap prioritization.** O\*NET documents role requirements and their scales in detail [O1]. LinkedIn Career Explorer suggests skills to add when changing roles [L5], but it works from the presence of skills rather than proficiency levels, and LinkedIn withdrew its skill assessments [L1].

**Coursera links roles, skills, and content, but individual proficiency-based gap reporting is not established by the reviewed sources.** Its learner-facing recommendations connect career goals with content [C1] [C4], while LevelSets are described in an organizational offering [C2].

**Self-rated skills are a recurring weakness.** Where verification is absent or limited (O\*NET, LinkedIn, roadmap.sh), the user's own judgment determines what counts as known. Pluralsight now advertises a standards-based verification option, but this does not by itself establish that every skill or role is covered by it [P5]. The literature review reports only a moderate correlation between self-evaluations and performance (Zell & Krizan, 2014), which makes this a relevant limitation for a system whose analysis begins with self-assessment.

## 8. Implications for CareerLens

The comparison suggests design directions. These are hypotheses that the project must test; they are not claims that CareerLens will outperform the reviewed systems. Feature availability, access conditions, and pricing may vary by product version, account type, or subscription.

| Observation in existing systems | Implication for CareerLens |
|---|---|
| Role requirements are well documented in O\*NET, with separate Importance and Level scales [O1] | Build target-role profiles from documented sources (ESCO, O\*NET) and keep importance and required level separate |
| Gap analysis is either missing (O\*NET, roadmap.sh) or based on skill presence only (LinkedIn) | Compare the user's proficiency level with the required level per skill and show the difference |
| Verification exists mainly in organization-oriented products (Pluralsight, Coursera LevelSets) | Include short checks for a limited set of skills in the MVP and mark which skills are verified and which are self-rated |
| Ordered paths and progress tracking exist in roadmap.sh and Pluralsight [R1] [P1] | Generate an ordered roadmap from the identified gaps and allow reassessment |
| Method details are proprietary in several products [L4] [P2] | Use transparent, documented prioritization rules and explain each recommendation |
| Some role-level assessment features are also positioned for organizational use [P3] | Design for individual students and early-career users, starting with a limited set of roles |
| Availability and pricing differ across products and account types | State access assumptions explicitly and avoid treating a feature as universally available |

The planned MVP scope in the project README (a limited set of roles, no claims of validated AI accuracy) is consistent with these observations. Whether the combination of features is useful to students must be evaluated in testing against a baseline, as set out in the evaluation plan.

## 9. Limitations of This Comparison

- **No hands-on testing.** Ratings come from public documentation and vendor or press descriptions. Screenshots or notes from using each product would strengthen the comparison and should be added if they are collected.
- **Features may differ by account type.** Several Coursera and Pluralsight features are described for organizational customers and may not be available to individual users.
- **Source age.** The descriptions of LinkedIn Career Explorer are from 2020 to 2023, and its current availability was not confirmed. LinkedIn's withdrawal of Skill Assessments shows how quickly such features can change.
- **Secondary sources.** Some historical details about LinkedIn Career Explorer, including the description of its skills-similarity score, rely on secondary reporting [L4]. Current availability of the standalone Career Explorer experience was not confirmed.
- **Pricing and access.** A complete pricing comparison was not conducted. Public availability, individual-account access, and organizational subscriptions are distinguished only where the reviewed sources support that distinction.
- **Ratings are judgments.** "Not evidenced" means a feature was not found in the reviewed pages, not that it does not exist.
- **Selection of systems.** Five systems cannot represent the whole market; other tools (for example, employer-side skills platforms) were not reviewed.

## 10. Sources

Sources reviewed in October 2026. Product features and access conditions can change; ratings reflect the evidence listed below and should not be interpreted as a hands-on product test.

**O\*NET OnLine**

- [O1] O\*NET OnLine. *Help: Scales, Ratings, and Standardized Scores.* https://www.onetonline.org/help/online/scales
- [O2] O\*NET OnLine. *Desk Aid.* (Copy hosted by Portland Community College.) https://www.pcc.edu/staff/tmaldona/wp-content/uploads/sites/114/2024/01/Onet-_aid.pdf

**LinkedIn**

- [L1] LinkedIn Help. *Skill Assessments – no longer available.* https://www.linkedin.com/help/learning/answer/a1690529
- [L2] LinkedIn Help. *Skills Match insight on jobs.* https://www.linkedin.com/help/linkedin/answer/a793433
- [L3] Microsoft Support. *Career Coach deprecation FAQs.* https://support.microsoft.com/en-us/topic/career-coach-deprecation-faqs-4d48c490-733a-49c9-ae7e-3135d2ce58f6
- [L4] Social Media Today. *LinkedIn adds new tools to help job seekers, including new career path insights* (2020). https://www.socialmediatoday.com/news/linkedin-adds-new-tools-to-help-job-seekers-including-new-career-path-insi/588064
- [L5] TechXplore. *LinkedIn's new tool helps users make a career change through overlapping skills* (2020). https://techxplore.com/news/2020-10-linkedin-tool-users-career-overlapping.amp
- [L6] Gulf News. *LinkedIn's new 'Career Explorer' tool to help professionals find jobs* (2020). https://gulfnews.com/amp/story/technology%2Fmedia%2Flinkedins-new-career-explorer-tool-to-help-professionals-find-jobs-1.1603976739379

**Coursera**

- [C1] Coursera Blog. *From Catalog to Compass: Introducing Personalized Recommendations to Guide Career Growth.* https://blog.coursera.org/from-catalog-to-compass
- [C2] Coursera for Government. *SkillSets and LevelSets.* https://www.coursera.org/government/skillsets
- [C3] Business Wire. *Coursera Announces Skill Tracks* (9 September 2025). https://secure.businesswire.com/news/home/20250909047985/en/Coursera-Announces-Skill-Tracks-Tailored-Data-backed-Learning-Solution-to-Accelerate-Critical-Skills-Development-Across-Functional-Teams
- [C4] Coursera. *Skills Graph and Skills Taxonomy methodology.* https://www.coursera.org/campus/skills-reports/campus/methodology

**roadmap.sh**

- [R1] roadmap.sh. *About.* https://roadmap.sh/about
- [R2] roadmap.sh. *AI Roadmap Generator.* https://roadmap.sh/ai
- [R3] roadmap.sh. *Developer Roadmaps.* https://roadmap.sh/roadmaps/
- [R4] roadmap.sh. *Get started.* https://roadmap.sh/get-started
- [R5] roadmap.sh. *Roadmaps for Teams.* https://roadmap.sh/teams

**Pluralsight**

- [P1] Pluralsight Help. *Taking a Skill IQ.* Updated February 19, 2026. https://help.pluralsight.com/hc/en-us/articles/24420144243604-Taking-a-Skill-IQ
- [P2] Pluralsight Help. *Assessments overview and comparison.* https://help.pluralsight.com/hc/en-us/articles/42596595693972-Assessments-overview-and-comparison
- [P3] Pluralsight. *Role IQ.* https://www.pluralsight.com/product/role-iq
- [P4] Pluralsight Help. *Features available on Pluralsight's mobile apps* (feature availability varies by plan). https://help.pluralsight.com/hc/en-us/articles/24350587963796-Features-available-on-Pluralsight-s-mobile-apps
- [P5] Pluralsight. *New Pluralsight features: Pluralsight AI MCP, Skill IQ Suite™, and enhanced analytics.* October 2026. https://www.pluralsight.com/resources/blog/news/2026-new-features-ai-mcp-skill-iq-suite
