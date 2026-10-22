# Literature Review

## 1. Introduction

CareerLens is a proposed intelligent skill gap analysis and personalized career recommendation system designed for students, recent graduates, and early-career professionals. Its main purpose is to help users understand the competencies required for a selected career, compare those requirements with their current skills, identify areas for improvement, and develop a personalized learning roadmap.

Career planning involves more than choosing a job title. Individuals need to understand their interests, existing competencies, occupational requirements, and opportunities for further development. A useful digital system should therefore connect career information with skill assessment and practical learning recommendations.

This literature review examines research and established frameworks related to occupational skills, career choice, competency-based recommendation systems, skill extraction from job advertisements, the accuracy of self-assessment, personalized learning, and usability evaluation. The findings are used to establish the theoretical foundation for CareerLens and to justify its proposed functionality.

## 2. Search Strategy and Scope

The review focuses on seven areas:

1. Occupational skill and competency frameworks.
2. Career choice and career development theories.
3. Personalized career recommendation and career guidance systems.
4. Competency-based course and learning recommendations.
5. Employability skills expected from graduates.
6. Skill identification from job advertisements and the accuracy of self-assessed skills.
7. Usability evaluation of interactive software systems.

The sources include peer-reviewed journal articles, conference proceedings, a scholarly book chapter, a master's thesis, and official competency frameworks. Publisher pages, institutional repositories, PubMed Central, and official framework websites were used to verify bibliographic metadata and compare the descriptions with the available abstracts. Where a full-text claim could not be confirmed from the available record, the review avoids presenting it as a definitive finding. Statements about each study are limited to what its published abstract and bibliographic record report; results are not generalized beyond the context in which they were obtained.

The review uses a thematic approach. Instead of simply listing publications, it compares their contributions, identifies limitations relevant to CareerLens, and explains how the findings inform the proposed system.

Official resources such as ESCO, O\*NET, and DigComp are included because they provide occupational and competency data. They are distinguished from academic publications and are not counted as peer-reviewed research articles. Brooke (1996) is a book chapter describing a questionnaire and is likewise not counted as a peer-reviewed article. The master's thesis is listed separately from peer-reviewed publications.

## 3. Literature Review

### 3.1 Occupational Skills and Competency Frameworks

ESCO (European Skills, Competences, Qualifications and Occupations) is a multilingual classification developed by the European Commission. It describes occupations, skills, competences, and qualifications and establishes relationships between occupations and the skills associated with them. This structure can support the creation of standardized occupational profiles for a career recommendation system.

O\*NET provides detailed information about occupations, including skills, knowledge, abilities, tasks, and work activities. An important feature of O\*NET is that its ratings represent different concepts. Each descriptor is associated with a scale such as Importance or Level. The Importance scale ranges from 1 to 5, while the Level scale ranges from 0 to 7. Because the scales cover different numerical ranges, a mean of 3.0 means something different on each, and O\*NET OnLine therefore reports standardized 0–100 scores. For example, a skill can be important to several occupations while the level of that skill required in each occupation differs substantially.

The Digital Competence Framework (DigComp), maintained by the European Commission's Joint Research Centre, provides a structured description of digital competence. It can inform the classification and assessment of digital skills, although its scope does not cover every technical competency required for every profession.

These resources demonstrate the value of structured skill descriptions and consistent terminology. At the same time, they have different purposes and measurement approaches. A system combining information from multiple frameworks must document how the information is mapped and interpreted.

**Implications for CareerLens:** ESCO and O\*NET can inform the definition of target-role skill profiles, while DigComp can support the organization of relevant digital competencies. The distinction between the Importance and Level scales in O\*NET suggests that CareerLens should keep "how important a skill is for a role" separate from "what level of the skill the role requires". CareerLens may introduce its own proficiency scale for user self-assessment, but this scale must be explicitly documented as a project design decision rather than presented as a universal standard.

### 3.2 Career Choice and Career Development

Lent, Brown, and Hackett (1994) introduced a social cognitive framework for understanding career interests, academic and career choices, and performance. Their work emphasizes factors such as self-efficacy, expected outcomes, personal goals, learning experiences, and environmental influences.

This perspective is important because career suitability cannot be determined by technical skills alone. Personal interests, confidence, prior experience, and contextual factors can also influence career decisions. A recommendation system that relies exclusively on a list of technical competencies may therefore provide an incomplete picture of a user's career preferences.

Dacre Pool and Sewell (2007) proposed the CareerEDGE model as a practical framework for graduate employability. Their work connects employability with areas such as career development learning, experience, degree-related knowledge and skills, generic skills, and emotional intelligence. The authors describe the relationships between the elements of the model as theoretical and note that further research is needed to test it. The model nevertheless provides a broader perspective on career readiness than technical knowledge alone.

These studies do not directly prescribe the architecture of a software-based skill gap analysis system. However, they provide a theoretical basis for considering both competencies and individual career development needs.

**Implications for CareerLens:** The system should distinguish between skill matching and overall career suitability. Its initial version can focus on comparing current skills with the requirements of a selected role. Additional factors, such as interests or experience, may be incorporated when their purpose and assessment method are clearly defined. The system should not claim to determine a user's ideal career solely from a proficiency score.

### 3.3 Personalized Career Recommendation and Career Guidance Systems

Qamhieh, Sammaneh, and Demaidi (2020) presented the Personalized Career-Path Recommender System (PCRS), which helps high-school students choose an engineering discipline. The system uses a fuzzy-logic approach and considers academic performance, personality type, and extracurricular skills. The association between personality type and engineering discipline was built using a sample of 1,250 engineering students, and the system was evaluated against a sample of 177 engineers. The authors examined the agreement between the recommendations generated by PCRS and the actual disciplines of the sample and report only slight agreement.

This result is significant for the design of CareerLens. It illustrates that generating personalized recommendations is not sufficient to establish their accuracy. Recommendation quality depends on the information provided to the system, the assumptions used by its model, and the way its outputs are evaluated. PCRS also addresses a different problem from CareerLens: it supports the choice of a study discipline for school students rather than skill gap analysis for students and early-career professionals.

Seesukong, Angskun, Keandoungchun, Thippongtorn, and Angskun (2024) presented CARIA, a personalized career recommender based on students' competencies and the skills required for each career, focused on digital technology and digital media careers. The system uses a novel similarity measure, modified Euclidean similarity, and compares it with other similarity measures, machine learning techniques, and GPT-4. The authors report a precision@10 of 0.83 for the modified Euclidean similarity, which outperformed the other techniques in their experiment. The stated objectives of CARIA include conducting a competency gap analysis.

CARIA is the closest study to CareerLens among those reviewed: it treats competency matching and gap analysis as a measurable recommendation task in a technology-related domain. However, results obtained using a particular dataset and evaluation procedure should not automatically be generalized to different users, occupations, or datasets.

José-García et al. (2023) introduced C3-IoC, an AI-based career guidance system that helps students explore IT career paths according to their level of education, skills, and prior experience. C3-IoC presents a novel similarity metric for relating existing job roles to a range of technical and non-technical skills and visualizes a network of job roles, placing the student within communities of related roles. The system uses text mining and machine learning to build its job-role representation.

C3-IoC is relevant because it combines technical and non-technical skills, targets the IT sector, and shows how the relationship between a student's profile and job roles can be presented visually. Its focus is on exploring career paths; it is not designed to produce a prioritized learning plan for one chosen role.

Together, these studies demonstrate several approaches to career recommendations: fuzzy-rule-based reasoning (PCRS), competency similarity (CARIA), and similarity-based job-role networks (C3-IoC). Fuzzy rules can represent expert-defined relationships, while similarity-based methods can provide a relatively direct comparison between user profiles and occupational profiles.

**Implications for CareerLens:** A transparent, similarity-based matching method is a reasonable candidate for the initial implementation. The system can compare a user's assessed competencies with the requirements of a selected role and explain which skills match and which require development. CARIA and C3-IoC suggest that technical and non-technical skills can be represented in one profile. Recommendation quality should be evaluated separately from usability.

### 3.4 Competency-Based Learning Recommendations

Beutling and Spahic-Bogdanovic (2024) presented a personalized course recommender that connects career goals with learning objectives through competencies. Their knowledge-based recommendation system uses the ESCO ontology, course descriptions, and a large language model to relate course content to the competencies required for careers in information systems. The system evaluates the relevance of a course by the number of job-related skills supported by its learning objectives and provides reasoning for the courses it proposes.

An important contribution of this work is the connection between career requirements and learning activities. A system that identifies a skill gap provides more practical value when it can also help the user identify relevant opportunities to improve that skill.

However, a course recommendation is only useful if its content supports the competency it claims to develop. Course descriptions may be incomplete, and a course may cover only part of a skill. In the related master's thesis, the same author reports that matching learning objectives to competencies accurately and efficiently remained a challenge (Beutling, 2023). Therefore, matching a course to a competency should not be treated as proof that the user will master that competency after completing the course.

**Implications for CareerLens:** The learning roadmap should connect identified skill gaps with relevant learning activities. Each recommendation should explain which skill it supports and why it is relevant to the selected role. Where possible, gaps should be prioritized according to their importance for the role and the user's current proficiency. The system should present its roadmap as guidance rather than a guarantee of employment or competency mastery.

### 3.5 Employability Skills and Skill Identification from Job Advertisements

Tushar and Sooraksa (2023) conducted a semi-systematic literature review of research on employability skills that employers seek in recent graduates. Their review covers literature published between 1990 and 2019 and aims to present a set of global employability skills and to identify how these skills change over time. The authors also report, citing earlier studies, that graduates continue to lack market-driven skills needed in the 21st-century workplace. This supports the need for career development activities that help individuals recognize and address areas for improvement, and it indicates that technical skills are only part of what employers expect.

Khaouja, Kassou, and Ghogho (2021) systematically reviewed 108 research articles on skill identification from online job advertisements. Because job postings are written as unstructured text, the skills they require must be extracted before they can be analyzed. The survey classifies prior work by the skill bases used, the type of extracted skills, the identification methods, the studied sector, and the granularity of identification, and it categorizes the applications of skill identification.

This work is relevant to the way CareerLens defines target-role profiles. Role requirements can be derived from structured frameworks such as ESCO and O\*NET, from job advertisements, or from a combination of both. Extracting skills automatically from job postings requires natural language processing and a skill base to which the extracted terms are mapped, which adds technical complexity and a source of error.

**Implications for CareerLens:** For the MVP, target-role profiles for a limited set of roles can be defined manually from documented sources (for example, ESCO, O\*NET, and a reviewed sample of job advertisements). Automatic skill extraction can be treated as a possible later extension, and its error rate would need to be evaluated before the results are shown to users. Transferable skills should be considered alongside technical skills.

### 3.6 Accuracy of Self-Assessed Skills

CareerLens starts from a self-assessment of the user's current skills, so the reliability of self-assessment directly affects the quality of the skill gap analysis. Zell and Krizan (2014) analyzed the correspondence between self-evaluations of ability (including academic ability, intelligence, language competence, medical skills, sports ability, and vocational skills) and objective performance measures across 22 meta-analyses. The mean correlation between self-evaluations and performance outcomes was moderate (M = .29, SD = .11), with individual meta-analytic effects ranging from .09 to .63. The relationship was stronger when self-evaluations were specific to a given domain rather than broad, and when performance tasks were objective, familiar, or low in complexity. The authors conclude that people have only moderate insight into their abilities.

A commentary on this study by Dunning and Helzer (2014) notes that the correlation coefficient is not the only way to measure accuracy and encourages researchers to examine measures of bias as well; the conclusions about self-assessment accuracy are therefore not final.

**Implications for CareerLens:** Self-rated proficiency alone should not be treated as an accurate measurement. CareerLens should ask users to rate specific skills rather than broad areas, and, where feasible, supplement self-ratings with short objective checks or evidence of experience. Because only a limited set of roles and checks is planned for the MVP, the system should state clearly which skills have been verified and which rest on self-assessment only. The effect of such checks on the quality of the results must be tested rather than assumed.

### 3.7 Usability Evaluation

Brooke (1996) introduced the System Usability Scale (SUS), a short questionnaire for evaluating perceived usability. The instrument contains ten items and produces a score on a 0–100 scale. It is widely used to gather standardized feedback about how users perceive an interactive system.

Bangor, Kortum, and Miller (2008) analyzed nearly ten years of SUS data collected on numerous products in all phases of the development lifecycle. Their study supports the usefulness of SUS as a practical usability assessment instrument and discusses the interpretation of its scores, including an adjective rating that correlates with a given score.

SUS measures perceived usability rather than the accuracy of career recommendations or the effectiveness of a learning roadmap. Therefore, a good SUS score alone would not demonstrate that CareerLens identifies the correct skill gaps or improves career outcomes.

**Implications for CareerLens:** Usability testing can ask participants to complete tasks such as selecting a career role, assessing current skills, interpreting a skill-gap report, and finding a relevant learning recommendation. SUS can then be used alongside task completion, observed difficulties, and qualitative feedback. Any scores and conclusions must be reported only after the evaluation has been conducted.

## 4. Comparative Analysis

The reviewed sources provide complementary foundations for the proposed system.

| Area | Main contribution | Limitation for CareerLens | Design implication |
|---|---|---|---|
| Occupational frameworks (ESCO, O\*NET, DigComp) | Structured descriptions of occupations and competencies | Frameworks differ in scope and measurement scales | Document skill selection and mapping; keep importance and level separate |
| Career development theory (Lent et al.; Dacre Pool & Sewell) | Explains personal and contextual influences on career choices | Does not provide a software recommendation algorithm; CareerEDGE is theoretical | Distinguish competency matching from overall career suitability |
| Career recommendation systems (PCRS, CARIA, C3-IoC) | Demonstrate fuzzy, similarity-based, and network-based approaches | Performance depends on data, domain, assumptions, and evaluation; PCRS targets school students | Start with an interpretable similarity-based matching method; evaluate its quality |
| Personalized course recommendations (Beutling & Spahic-Bogdanovic) | Connect career requirements with learning activities | Course-to-skill matching does not guarantee skill mastery | Explain how each learning recommendation relates to a gap |
| Employability and skill extraction (Tushar & Sooraksa; Khaouja et al.) | Show which skills employers expect and how skills can be identified in job ads | Automatic extraction adds complexity and error | Use manually defined role profiles in the MVP; include transferable skills |
| Self-assessment accuracy (Zell & Krizan) | Shows that self-rated ability correlates only moderately with performance | Findings are aggregate and domain-dependent | Use specific skill items and add objective checks where feasible |
| Usability evaluation (Brooke; Bangor et al.) | Provides methods for collecting user feedback | Perceived usability does not measure recommendation accuracy | Evaluate usability and recommendation quality separately |

The comparison suggests that CareerLens should not depend on a single source or method. Occupational frameworks can supply reference information, career development research can inform the interpretation of recommendations, research on self-assessment can shape how skills are collected, and usability methods can help evaluate the resulting application.

## 5. Research Gap and Project Positioning

The reviewed literature provides foundations for occupational skill representation, career recommendation, competency-based learning, skill extraction, self-assessment, and usability evaluation. However, these areas address different parts of the career development process.

Career recommendation systems focus mainly on suggesting careers or study directions, while competency frameworks describe occupations and skills. CARIA includes competency gap analysis but is evaluated mainly on the quality of career recommendations in digital technology and media, and C3-IoC supports exploration of IT career paths. Personalized learning recommenders connect competencies with educational activities. Research on self-assessment indicates that self-rated skills should be treated with caution. Usability studies provide methods for evaluating interactions with software. These contributions can inform a unified workflow, but their existence does not establish that CareerLens will outperform existing systems.

CareerLens is therefore positioned as a proposed integrated workflow for students, recent graduates, and early-career professionals. The workflow consists of:

1. Selecting a target career role.
2. Assessing the user's current skills, with specific skill items and, where feasible, short checks that supplement self-assessment.
3. Comparing current skills with a documented target-role profile.
4. Identifying and prioritizing skill gaps.
5. Recommending learning activities related to those gaps.
6. Tracking progress and allowing reassessment.

The project's practical contribution is to design and evaluate this workflow using transparent skill-matching rules and understandable explanations. Its novelty should be assessed against existing systems through a separate comparison rather than assumed from the combination of familiar features.

The central research question is:

**How can a transparent skill-matching approach help students and early-career professionals identify skill gaps and plan learning activities aligned with a selected career role?**

The project can investigate this question by implementing a documented matching method, testing whether users understand the skill-gap results, and evaluating the usability and recommendation quality of the proposed workflow.

## 6. Limitations

This review combines academic research with official occupational and competency resources. These sources have different purposes and should not be interpreted as equivalent evidence. Frameworks describe occupational or competency information, while empirical studies evaluate particular methods in specific contexts.

The reviewed career recommendation systems may use different input data, target populations, recommendation methods, and evaluation metrics. Their reported results cannot automatically be generalized to CareerLens. Several of the sources (Lent et al., 1994; Dacre Pool & Sewell, 2007; Brooke, 1996) are older or theoretical and do not address skill gap analysis directly.

The proposed proficiency scale, skill prioritization rules, learning recommendations, and user interface also require explicit documentation. Their effectiveness must be evaluated using appropriate data rather than inferred from the literature alone.

Finally, the present review provides a focused foundation rather than an exhaustive systematic review of every career recommendation or skill gap analysis system. A reproducible systematic review would require a documented search protocol, databases searched, search strings, inclusion and exclusion criteria, and a record of the screening process.

## 7. Conclusion

The reviewed literature supports the use of structured occupational information, competency-based matching, personalized learning recommendations, careful treatment of self-assessment, and usability evaluation as foundations for CareerLens.

ESCO and O\*NET can inform the definition of occupational skill profiles, while DigComp can help organize relevant digital competencies. Career development theory highlights the importance of personal and contextual factors. Existing recommendation systems (PCRS, CARIA, C3-IoC) demonstrate possible matching approaches, and personalized course recommendation research shows how skill gaps can be connected with learning activities. Research on skill identification and employability shows how role requirements can be derived and why transferable skills matter, while evidence on self-assessment motivates objective checks. Usability research provides practical methods for evaluating the proposed interface.

Based on these findings, CareerLens will investigate a transparent approach to comparing user skills with target-role requirements and translating identified gaps into actionable learning recommendations. The system's usefulness must be demonstrated through implementation and evaluation.

## References

### Academic Publications

1. Qamhieh, M., Sammaneh, H., & Demaidi, M. N. (2020). PCRS: Personalized Career-Path Recommender System for Engineering Students. *IEEE Access, 8*, 214039–214049. https://doi.org/10.1109/ACCESS.2020.3040338

2. Seesukong, S., Angskun, T., Keandoungchun, N., Thippongtorn, A., & Angskun, J. (2024). CARIA: A Personalized Career Recommender Based on Individual Competency Similarity Measure. *International Journal of Information and Communication Technology Education, 20*(1), 1–24. https://doi.org/10.4018/IJICTE.356499

3. José-García, A., Sneyd, A., Melro, A., Ollagnier, A., Tarling, G., Zhang, H., Stevenson, M., Everson, R., & Arthur, R. (2023). C3-IoC: A career guidance system for assessing student skills using machine learning and network visualisation. *International Journal of Artificial Intelligence in Education, 33*(4), 1092–1119. https://doi.org/10.1007/s40593-022-00317-y

4. Beutling, N., & Spahic-Bogdanovic, M. (2024). Personalised Course Recommender: Linking Learning Objectives and Career Goals through Competencies. *Proceedings of the AAAI Symposium Series, 3*(1), 72–81. https://doi.org/10.1609/aaaiss.v3i1.31185

5. Khaouja, I., Kassou, I., & Ghogho, M. (2021). A Survey on Skill Identification From Online Job Ads. *IEEE Access, 9*, 118134–118153. https://doi.org/10.1109/ACCESS.2021.3106120

6. Tushar, H., & Sooraksa, N. (2023). Global employability skills in the 21st century workplace: A semi-systematic literature review. *Heliyon, 9*(11), e21023. https://doi.org/10.1016/j.heliyon.2023.e21023

7. Zell, E., & Krizan, Z. (2014). Do people have insight into their abilities? A metasynthesis. *Perspectives on Psychological Science, 9*(2), 111–125. https://doi.org/10.1177/1745691613518075

8. Dunning, D., & Helzer, E. G. (2014). Beyond the correlation coefficient in studies of self-assessment accuracy: Commentary on Zell & Krizan (2014). *Perspectives on Psychological Science, 9*(2), 126–130. https://doi.org/10.1177/1745691614521244

9. Lent, R. W., Brown, S. D., & Hackett, G. (1994). Toward a unifying social cognitive theory of career and academic interest, choice, and performance. *Journal of Vocational Behavior, 45*(1), 79–122. https://doi.org/10.1006/jvbe.1994.1027

10. Dacre Pool, L., & Sewell, P. (2007). The key to employability: Developing a practical model of graduate employability. *Education + Training, 49*(4), 277–289. https://doi.org/10.1108/00400910710754435

11. Bangor, A., Kortum, P. T., & Miller, J. T. (2008). An empirical evaluation of the System Usability Scale. *International Journal of Human–Computer Interaction, 24*(6), 574–594. https://doi.org/10.1080/10447310802205776

### Book Chapter

12. Brooke, J. (1996). SUS: A “quick and dirty” usability scale. In P. W. Jordan, B. Thomas, B. A. Weerdmeester, & I. L. McClelland (Eds.), *Usability Evaluation in Industry* (pp. 189–194). Taylor & Francis. https://doi.org/10.1201/9781498710411-35

### Official Frameworks and Data Resources

13. European Commission. (n.d.). *European Skills, Competences, Qualifications and Occupations (ESCO).* https://esco.ec.europa.eu/en

14. O\*NET Resource Center. (n.d.). *O\*NET Database.* https://www.onetcenter.org/database.html

15. O\*NET OnLine. (n.d.). *Scales, Ratings, and Standardized Scores.* https://www.onetonline.org/help/online/scales

16. European Commission, Joint Research Centre. (n.d.). *The Digital Competence Framework (DigComp).* https://joint-research-centre.ec.europa.eu/scientific-activities/key-competences-lifelong-learning/digital-competence-framework-digcomp_en

### Thesis

17. Beutling, N. (2023). *Personalised Course Recommendations in the Domain of Information Systems* [Master's thesis]. FHNW University of Applied Sciences and Arts Northwestern Switzerland. https://irf.fhnw.ch/handle/11654/48830