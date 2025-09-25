# shared-prescription-search-support
Welcome! This repository contains the key documentation for using and integrating with PSS Project.

# Integration Guide for **Shared NIHDI PSS Web Components**

This document explains how to integrate and use the web components available in the package `@smals-belgium-shared/shared-nihdi-pss-web-components`.

---

## 1. Prerequisites: Obtain a valid eHealth OAuth token

- To work with the **acceptance environment** (`configName = 'acc'`), you need a **valid eHealth OAuth token** linked to a **NIHDI number**.  
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

The package contains **3 web components**:  

1. **`pss-amb-get-support-parameters`**  
   - This is the initial component that produces an **output** (support parameters).  
   - This output must then be reused by the next two components.  

2. **`pss-amb-recommendation`**  
   - Consumes the output of the first component.  
   - Provides recommendations based on the given parameters.  

3. **`pss-amb-summary`**  
   - Also consumes the output of the first component.  
   - Provides a summary view based on the generated data.  

👉 This design gives you **flexibility in managing the presentation flow**.

---

## 5. Very simplified example usage (not working)

```html
<html>
  <head>
    <script type="module" src="path/to/shared-nihdi-pss-web-components.js"></script>
  </head>
  <body>
    <!-- 1. Generate support parameters -->
    <pss-amb-get-support-parameters id="supportParams"></pss-amb-get-support-parameters>

    <!-- 2. Recommendations -->
    <pss-amb-recommendation 
      parameters="supportParams.output">
    </pss-amb-recommendation>

    <!-- 3. Summary -->
    <pss-amb-summary 
      parameters="supportParams.output">
    </pss-amb-summary>
  </body>
</html>
```


## Documentation & Resources
- [PSS API Cookbook](https://github.com/smals-belgium/shared-prescription-search-support/blob/master/PSS_API_Cookbook_v1.2.pdf)
  - Domain: Antimicrobial, Radiology
  - Version: 1.2
  - Official link: [Link](https://confluence.smals.be/pages/viewpage.action?pageId=460597855&spaceKey=HCHAUDIT&title=PSS%2BAntimicrobial&preview=/460597855/471842118/PSS_API_Cookbook_v1.2.pdf)
  - Last updated: 01/04/2025
- [PSS Integration Guide](https://github.com/smals-belgium/shared-prescription-search-support/blob/master/PSS%20Integration%20guide_Fin.pdf)
  - Domain: Antimicrobial, Radiology
  - Version: 1.4
  - Official link: [Link](https://confluence.smals.be/pages/viewpage.action?pageId=460597855&spaceKey=HCHAUDIT&title=PSS%2BAntimicrobial&preview=/460597855/471842094/PSS%20Integration%20guide_Fin.pdf)
  - Last updated: 13/05/2025
- [PSS WebComponents Cookbook Guide](https://github.com/smals-belgium/shared-prescription-search-support/blob/master/PSS_WebComponents_Cookbook_v1.pdf)
  - Domain: Antimicrobial
  - Version: 1.0
  - Official link: [Link](https://confluence.smals.be/pages/viewpage.action?pageId=460597855&spaceKey=HCHAUDIT&title=PSS%2BAntimicrobial&preview=/460597855/471842142/PSS_WebComponents_Cookbook_v1.pdf)
  - Last updated: 17/09/2025
- [PSS Indication Codes](https://github.com/smals-belgium/shared-prescription-search-support/blob/master/indication_codes%20(1).xlsx)
  - Domain: Antimicrobial
  - Version: 1.0
  - Official link: [Link](https://confluence.smals.be/pages/viewpage.action?pageId=460597855&spaceKey=HCHAUDIT&title=PSS%2BAntimicrobial&preview=/460597855/476131352/indication_codes.xlsx)
  - Last updated: 04/07/2025
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
  - Version: 0.0.1
  - Official link: [Link](https://www.npmjs.com/package/@smals-belgium-shared/shared-nihdi-pss-web-components)
  - Last updated: 19/08/2025
- Registration Criteria
  - Domain: Antimicrobial
  - Version: 1.0
  - Official link: [Published on RIZIV website](https://eur03.safelinks.protection.outlook.com/?url=https%3A%2F%2Fwww.riziv.fgov.be%2FSiteCollectionDocuments%2FPSS_Antimicrobial_Criteria_list_for_software_registration_Release_Version1_0.xlsx&data=05%7C02%7Cjeroen.dewilde%40riziv-inami.fgov.be%7C29c54d202af548bbacdb08dd9e0ca488%7C66c008a4b56549a993c9c1e64cad2e11%7C0%7C1%7C638840499977060738%7CUnknown%7CTWFpbGZsb3d8eyJFbXB0eU1hcGkiOnRydWUsIlYiOiIwLjAuMDAwMCIsIlAiOiJXaW4zMiIsIkFOIjoiTWFpbCIsIldUIjoyfQ%3D%3D%7C0%7C%7C%7C&sdata=S%2B1fqPZ8FWdWXEj2b0l89E1%2FvNpfEzHMp3UVYpEAQi0%3D&reserved=0)
  - Last updated: 28/05/2025
