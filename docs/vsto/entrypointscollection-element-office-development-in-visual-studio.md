---
title: "&lt;entryPoint&gt;, &#233;l&#233;ment (d&#233;veloppement Office dans Visual Studio)"
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
  - "<EntryPointsCollection>, élément"
  - "manifestes d’application (développement Office dans Visual Studio), élément <entryPointsCollection>"
  - "entryPointsCollection, élément"
ms.assetid: da386d67-e45f-467c-a9ba-9b8451b520eb
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# &lt;entryPoint&gt;, &#233;l&#233;ment (d&#233;veloppement Office dans Visual Studio)
  L’élément `entryPointsCollection` de l’espace de noms `vstav3`  contient tous les éléments `entryPoints` associés aux solutions Office.  
  
## Syntaxe  
  
```  
<entryPointsCollection>  
  <entryPoints>  
    <entryPoint>  
    </entryPoint>  
    <entryPoint>  
    </entryPoint>  
    <entryPoint>  
    </entryPoint>  
  </entryPoints>  
</entryPointsCollection>  
```  
  
## Éléments et attributs  
 L’élément `entryPointsCollection` est obligatoire et se trouve dans l’espace de noms `vstav3`. Les éléments enfants doivent aussi se trouver dans cet espace de noms. Un seul élément `entryPointsCollection` est défini dans un manifeste d’application.  
  
 L’élément `entryPointsCollection` ne comporte pas d’attributs.  
  
 `entryPointsCollection` comporte les éléments suivants.  
  
### entryPoints  
 Obligatoire. Le rôle de l’élément `entryPoints` dans l’espace de noms `vstav3`  est défini dans [Élément &#60;entryPoint&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md).  
  
## Exemple de personnalisation au niveau du document  
  
### Description  
 L’exemple de code suivant illustre l’élément `entryPointsCollection` d’un manifeste d’application pour une solution au niveau du document déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:entryPointsCollection> <vstav3:entryPoints> <vstav3:entryPoint class="ContosoExcelWorkbook.ThisWorkbook"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet1"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet2"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet3"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints> </vstav3:entryPointsCollection>  
```  
  
## Exemple de complément VSTO  
  
### Description  
 L’exemple de code suivant illustre l’élément `entryPointsCollection` d’un manifeste d’application pour une solution au niveau du document déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:entryPointsCollection> <vstav3:entryPoints> <vstav3:entryPoint class="ContosoOutlookAddIn.ThisAddIn"> <assemblyIdentity name="ContosoOutlookAddIn" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints> </vstav3:entryPointsCollection>  
```  
  
## Exemple de déploiement de plusieurs projets  
  
### Description  
 L’exemple de code suivant illustre un élément `entryPointsCollection` de manifeste d’application pour le déploiement de plusieurs projets contenant deux solutions Office. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:entryPointsCollection> <vstav3:entryPoints id="ContosoExcel"> <vstav3:entryPoint class="ContosoExcelWorkbook.ThisWorkbook"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet1"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet2"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet3"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints> <vstav3:entryPoints id="ContosoOutlook"> <vstav3:entryPoint class="ContosoOutlookAddIn.ThisAddIn"> <assemblyIdentity name="ContosoOutlookAddIn" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints> </vstav3:entryPointsCollection>  
```  
  
## Voir aussi  
 [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  