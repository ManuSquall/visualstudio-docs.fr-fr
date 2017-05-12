---
title: "&#201;l&#233;ment &lt;addIn&gt; (D&#233;veloppement Office dans Visual Studio)"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "manifestes d’application (développement Office dans Visual Studio), <addIn> (élément)"
  - "addin (élément)"
  - "<addin> (élément)"
ms.assetid: 4abec4c3-8c7c-4b2b-9128-79fa4e863281
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# &#201;l&#233;ment &lt;addIn&gt; (D&#233;veloppement Office dans Visual Studio)
  L’élément `addin` de l’espace de noms `vstav3`  contient des informations propres aux compléments Microsoft Office VSTO et aux personnalisations au niveau du document développés avec Visual Studio.  
  
## Syntaxe  
  
```  
<addIn>  
  <entryPointsCollection>  
    <entryPoints>  
      <entryPoint>  
      </entryPoint>  
    </entryPoints>  
  </entryPointsCollection>  
  <update></update>  
  <postActions>  
    <postAction>  
      <postActionData>  
      </postActionData>  
    <postAction>  
  </postActions>  
  <application>  
    <customization>  
    </customization>  
  </application  
</addIn>  
```  
  
## Éléments et attributs  
 L’élément `addin` de l’espace de noms `vstav3`  contient des informations sur la solution Office et l’application Microsoft Office. Cet élément doit être dans l’espace de noms suivant : `vstav3=urn:schemas-microsoft-com:vsta.v3`. Les éléments enfants doivent également être dans cet espace de noms.  
  
 L’élément `addin` ne possède pas d’attributs.  
  
 L’élément `addin` possède les éléments enfants suivants :  
  
### entryPoints  
 Obligatoire. L’élément `entryPoints` est décrit dans [Élément &#60;entryPoint&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md).  
  
### update  
 Obligatoire. L’élément `update` est décrit dans [&#60;update&#62;, élément &#40;développement Office dans Visual Studio&#41;](../vsto/update-element-office-development-in-visual-studio.md).  
  
### postActions  
 Facultatif. L’élément `postActions` est décrit dans [Élément &#60;postActions&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/postactions-element-office-development-in-visual-studio.md).  
  
### application  
 Obligatoire. L’élément `application` est décrit dans [Élément &#60;application&#62; &#40;Développement Office dans Visual Studio&#41;](../vsto/application-element-office-development-in-visual-studio.md).  
  
## Exemple de personnalisation au niveau du document  
  
### Description  
 L’exemple de code suivant illustre l’élément `addin` dans une solution Office au niveau du document déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:addIn xmlns:vstav3="urn:schemas-microsoft-com:vsta.v3"> <vstav3:entryPointsCollection> <vstav3:entryPoints> <vstav3:entryPoint class="ContosoExcelWorkbook.ThisWorkbook"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet1"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet2"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet3"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints> </vstav3:entryPointsCollection> <vstav3:update enabled="true"> <vstav3:expiration maximumAge="7" unit="days" /> </vstav3:update> <vstav3:application> <vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization> </vstov4:customizations> </vstav3:application> </vstav3:addIn>  
```  
  
## Exemple de complément VSTO  
  
### Description  
 L’exemple de code suivant illustre l’élément `addin` dans une solution Office de niveau application déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:addIn xmlns:vstav3="urn:schemas-microsoft-com:vsta.v3"> <vstav3:entryPointsCollection> <vstav3:entryPoints> <vstav3:entryPoint class="ContosoOutlookAddIn.ThisAddIn"> <assemblyIdentity name="ContosoOutlookAddIn" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints> </vstav3:entryPointsCollection> <vstav3:update enabled="true"> <vstav3:expiration maximumAge="7" unit="days" /> </vstav3:update> <vstav3:application> <vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization> </vstov4:customizations> </vstav3:application> </vstav3:addIn>  
```  
  
## Voir aussi  
 [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  