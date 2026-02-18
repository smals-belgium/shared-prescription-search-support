# shared-prescription-search-support
Welcome! This repository contains the key documentation for using and integrating with PSS Project.

# SSO Registration

- [SSO Registration Deadline](https://github.com/smals-belgium/shared-prescription-search-support/blob/master/SSO-Registration.md)

# Integration Guide for **Shared NIHDI PSS Web Components**

This document explains how to integrate and use the web components available in the package [NPM package](https://www.npmjs.com/package/@smals-belgium-shared/shared-nihdi-pss-web-components).

---

## 1. Prerequisites: Obtain a valid eHealth OAuth token

- To work with the **acceptance environment** (`configName = 'acc'`), you need a **valid eHealth OAuth token with audience “nihdi-pss-api”** linked to a **NIHDI number**.  
- If you don’t have this token yet, you must contact **eHealth**.  

👉 In the meantime, you can continue integration using the **demo environment** (`configName = 'demo'`).

---

## 2. Install the web components package

### Option 1: via **npm**
```bash
npm install @smals-belgium-shared/shared-nihdi-pss-web-components
```

### Option 2: via **CDN**

You can also load the web components directly from a [CDN](https://cdn.jsdelivr.net/npm/@smals-belgium-shared/shared-nihdi-pss-web-components@latest)

---

## 3. Complete documentation

Full documentation is available on GitHub:  
🔗 [https://github.com/smals-belgium/shared-prescription-search-support](https://github.com/smals-belgium/shared-prescription-search-support)

---

## 4. Available web components

The package contains **4 web components**:  

1. **`pss-amb-consent`**  
   - The component displays two checkboxes: one mandatory for accepting the user conditions and privacy statement, and one optional for consenting to statistics collection.
   - The mandatory consent must be given before the user can access or use any part of the PSS workflow.
     
2. **`pss-amb-get-support-parameters`**  
   - This is the initial component that produces an **output** (support parameters).  
   - This output must then be reused by the next two components.  

3. **`pss-amb-recommendation`**  
   - Consumes the output of the first component.  
   - Provides recommendations based on the given parameters.  

4. **`pss-amb-summary`**  
   - Also consumes the output of the first component.  
   - Provides a summary view based on the generated data.  

👉 This design gives you **flexibility in managing the presentation flow**.

---

## 5. A full integration (with demo mode) on:
[Example](https://cdn.jsdelivr.net/npm/@smals-belgium-shared/shared-nihdi-pss-web-components@latest/example_PSSa.html)

### From demo to real EPD integration (short version)

To evolve the demo example into a production-ready integration:

1. **Handle the dependency properly**  
   Import the web components, fonts and icons yourself (CDN for demo, local build for production).

2. **Use a real eHealth token**  
   Replace the demo `getAccessToken()` with your IAM Connect flow returning a valid JWT (audience: `nihdi-pss-api`).

3. **Switch environments**  
   `configName = "demo"` → `"acc"` → `"prod"`.

4. **Set the correct userLanguage**  
   Provide `"nl"` or `"fr"` so UI labels match your EPD context.

5. **Connect with your EPD data**  
   Use the `parameters` event to match PSS codes with patient data, pass the resulting `supportResponse` to the summary and recommendation components, and handle `userConclusionSubmitted` to store the final recommendation.

➡️ **More detailed instructions can be found in the Web Components Cookbook.**

---

## Documentation & Resources
- [PSS API Cookbook](https://github.com/smals-belgium/shared-prescription-search-support/blob/master/PSS_API_Cookbook_v1.2.pdf)
  - Domain: Antimicrobial, Radiology
  - Version: 1.2
  - Official link: [Link](https://confluence.smals.be/pages/viewpage.action?pageId=460597855&spaceKey=HCHAUDIT&title=PSS%2BAntimicrobial&preview=/460597855/471842118/PSS_API_Cookbook_v1.2.pdf)
  - Last updated: 01/04/2025
- [PSS Integration Guide](https://github.com/smals-belgium/shared-prescription-search-support/blob/master/PSS_Integration_guide_v1.6.pdf)
  - Domain: Antimicrobial, Radiology
  - Version: 1.6
  - Official link: [Link](https://confluence.smals.be/pages/viewpage.action?pageId=460597855&spaceKey=HCHAUDIT&title=PSS%2BAntimicrobial&preview=/460597855/471842094/PSS%20Integration%20guide_Fin.pdf)
  - Last updated: 03/12/2025
- [PSS WebComponents Cookbook Guide](https://github.com/smals-belgium/shared-prescription-search-support/blob/master/PSS_WebComponents_Cookbook_v1.1.pdf)
  - Domain: Antimicrobial
  - Version: 1.1
  - Official link: [Link](https://confluence.smals.be/pages/viewpage.action?pageId=460597855&spaceKey=HCHAUDIT&title=PSS%2BAntimicrobial&preview=/460597855/471842142/PSS_WebComponents_Cookbook_v1.pdf)
  - Last updated: 03/12/2025
- [PSS Indication Codes](https://github.com/smals-belgium/shared-prescription-search-support/blob/master/indication_codes_v1.1.xlsx)
  - Domain: Antimicrobial
  - Version: 1.1
  - Official link: [Link](https://confluence.smals.be/pages/viewpage.action?pageId=460597855&spaceKey=HCHAUDIT&title=PSS%2BAntimicrobial&preview=/460597855/476131352/indication_codes.xlsx)
  - Last updated: 05/12/2025
- [PSS Respiratory Codes](https://github.com/smals-belgium/shared-prescription-search-support/blob/master/Codeboek_Luchtweginfecties%20Versie%203.0%20%20%20.xlsx)
  - Domain: Antimicrobial
  - Version: 3.0
  - Last updated: 18/02/2026
- [PSS Urinary Codes](https://github.com/smals-belgium/shared-prescription-search-support/blob/master/Codeboek_Urineweginfecties%20Versie%203.0.xlsx)
  - Domain: Antimicrobial
  - Version: 3.0
  - Last updated: 18/02/2026
- API PSS 
  - Domain: Antimicrobial, Radiology
  - Version: 1.0
  - Official link: [Link](https://portal.api.ehealth.fgov.be/api-details?apiId=a1977abb-7348-41bf-bd8f-3a7fc2f26e58&managerId=1&swaggerVersion=3.0&type=rest&usage=api&Itemid=171&catalogModuleId=120#methods)
- FHIR Implementation Guide
  - Domain: Antimicrobial, Radiology
  - Version: 1.0
  - Official link: [Published on eHealth](https://www.ehealth.fgov.be/standards/fhir/pss/artifacts.html)
  - Last updated: 14/05/2025
- Registration for FHIR Test Cases
  - Domain: Antimicrobial, Radiology
  - Official link: [Link](https://fhir-testserver.be/index.php/registration_form)
- FHIR testing and procedures information	
  - Domain: Antimicrobial, Radiology
  - Version: 1.0
  - Official link: [Link](https://docs.google.com/presentation/d/1mZEasXjsMlOKJKt5jRoWcZc2tCKtnH4T/edit?slide=id.p1#slide=id.p1)
  - Last updated: 15/06/2023
- Web Component PSS
  - Domain: Antimicrobial
  - Version: 1.0.1
  - Official link: [Link](https://www.npmjs.com/package/@smals-belgium-shared/shared-nihdi-pss-web-components)
  - Last updated: 04/12/2025
- Registration Criteria
  - Domain: Antimicrobial
  - Version: 1.5
  - Official link: [Link](https://github.com/smals-belgium/shared-prescription-search-support/blob/master/PSS%20Antimicrobial%20-%20Criteria%20list%20for%20software%20registration%20-Release%20Version%201.5.xlsx)
  - Last updated: 08/12/2025
