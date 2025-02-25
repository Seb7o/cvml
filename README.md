# CVML – CV Markup Language

CVML is a work-in-progress project aimed at defining a YAML-based structure for creating CVs (curriculum vitae). The project also includes the beginnings of an editor built with Vue and Tailwind CSS to help you build and validate your CVs in real time. Note that the editor is still in its early stages and may need further improvements—I'm not a front-end developer, so please bear with its imperfections.

---

## Overview

CVML stands for CV Markup Language. It defines a comprehensive YAML structure for representing your professional details, experience, education, skills, and more. The project is built around a JSON Schema (see [schema.json](schema.json)) that validates the structure of your CV file.

---

## Motivation

I created CVML out of frustration with the current recruitment game. Here are some key reasons behind this project:

- **Inconsistent Designs:** Recruiters often receive resumes with thousands of different designs and formats. This lack of standardization makes it hard to quickly find the relevant information.
- **Unclear ATS Standards:** You never truly know how Applicant Tracking Systems (ATS) work, which can lead to candidates being overlooked if their resumes aren't perfectly tailored.
- **Standardized Data:** By storing resume data in a standardized YAML format, CVML ensures that all resumes look the same when rendered, making it easier for recruiters to find the necessary information.
- **Customizable Presentation:** Recruiters can customize how they view resumes without relying on varied designs from different candidates.
- **Lightweight Files:** Using YAML results in lighter files that are easily readable by both humans and programs.
- **Improved ATS Compatibility:** With well-structured data, resumes can be fully interpreted by ATS, reducing the risk of candidates being rejected due to formatting issues.

---

## Integrity and Security

One known drawback of using plain text formats like YAML is that files can be easily altered. To address this, it would be ideal to include a checksum field in the CVML file. This checksum could be signed by trusted providers to ensure the file's integrity. Although I currently don't have the capability to implement such a system—being no trusted authority—I plan to explore this feature in future releases.

---

## Schema

The CVML schema is defined in a JSON file to ensure consistency and validity. The schema includes the following sections:

- **General Information:** Version and title of the CV.
- **Personal Info:** Basic personal details such as name, email, phone, and more.
- **Experience & Education:** Lists of professional experiences and educational qualifications.
- **Skills & Certifications:** Technical and soft skills, along with certifications.
- **Languages & Projects:** Languages known and projects undertaken.
- **Hobbies:** A list of personal interests and hobbies.

For the complete schema, refer to [schema.json](schema.json) which outlines all the properties and their requirements.  
citeturn1file0

---

## Editor (Work in Progress)

The project also includes the beginnings of a web-based editor built with Vue and Tailwind CSS to facilitate the creation and editing of CVML files. This editor is still in its infancy and is far from perfect, but it serves as a starting point for future improvements.

### Editor Screenshot

![CVML Editor Screenshot](screenshots/cvml_editor.png)

*Note: The editor is a work in progress and may not reflect the final user experience.*

---

## Usage

1. **Defining Your CV in YAML:**

   Create your CV file using the CVML structure defined in the JSON schema. This file should follow the required format to ensure validation.

2. **Validating Your CV:**

   Use your preferred JSON Schema validation tool to check your CV file against the schema provided in `schema.json`.

3. **Editing with the Editor (Optional):**

   If you wish to use the editor, run the Vue application to start experimenting with the interface.  
   *(Further instructions on setting up and running the editor will be provided as the project evolves.)*

---

## Roadmap

- **Schema Enhancements:** Further refine and expand the YAML structure for additional sections.
- **Checksum and File Integrity:** Explore adding a checksum field signed by trusted providers to secure the CV file against unauthorized alterations.
- **Editor Improvements:** Enhance the editor functionality, improve UI/UX, and add real-time validation.
- **ATS Integrations:** Develop plugins or integrations for popular Applicant Tracking Systems (ATS) to ensure smoother processing of CVML files. Although my knowledge about ATS integrations is limited, contributions from ATS developers would be amazing.
- **Documentation:** Continue to update this README and other documentation as features are developed.

---

## Contributing

CVML is envisioned as a standard developed by the community—a collective effort to improve how resumes are structured and processed. Your ideas and contributions are invaluable, whether you're a developer, a recruiter, or simply someone with innovative thoughts on recruitment standards. Here's how you can help:

- **Share Your Ideas:** Whether it's an improvement to the schema, suggestions for the editor, or insights from recruitment professionals, every idea is welcome.
- **Report Issues:** Found a bug or have a feature request? Please open an issue in the repository.
- **Collaborate on Enhancements:** Fork the repository, make your changes, and submit a pull request. Contributions can range from schema enhancements to front-end improvements.
- **Recruitment Expertise:** I don't work in recruitment, so insights from recruiters are especially appreciated. Your feedback can help make CVML more useful and exhaustive.
- **Collective Standardization:** By working together, we can build a standard that ensures resumes are clear, consistent, and optimized for both human recruiters and ATS systems.

Together, we can create a robust and standardized CV format that benefits job seekers and recruiters alike.

---

## License

This project is open source and available under the [MIT License](LICENSE).

---

## Acknowledgements

Thank you for checking out CVML! If you have any suggestions or feedback, please open an issue in the repository.

Enjoy crafting your CVs with CVML!