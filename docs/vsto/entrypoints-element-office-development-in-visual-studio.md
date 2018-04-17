---
title: '&lt;EntryPoint&gt; élément (développement Office dans Visual Studio) | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <entryPoints> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a620dae22e6fd67e3d880cbd87e8883911f28845
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ltentrypointsgt-element-office-development-in-visual-studio"></a>&lt;EntryPoint&gt; élément (développement Office dans Visual Studio)
  L’élément `entryPoints` de l’espace de noms `vstav3` contient tous les éléments `entryPoint` associés à une solution Office.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<entryPoints>  
    <entryPoint>  
    </entryPoint>  
    <entryPoint>  
    </entryPoint>  
    <entryPoint>  
    </entryPoint>  
</entryPoints>  
```  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 L’élément `entryPoints` est obligatoire et se trouve dans l’espace de noms `vstav3` . Il existe un seul élément `entryPoints` défini dans un manifeste de l’application pour chaque solution Office. Par exemple, si vous déployez trois solutions Office dans un déploiement à projets multiples, il existe trois éléments `entryPoints` dans le manifeste de l’application.  
  
 L’élément `entryPoints` comporte l’attribut suivant.  
  
|Attribut|Description|  
|---------------|-----------------|  
|ID|Obligatoire pour un déploiement à projets multiples. Nom de la solution Office. L’ID ne peut pas contenir le symbole égal (=).|  
  
 `entryPoints` comporte les éléments suivants.  
  
### <a name="entrypoint"></a>entryPoint  
 Obligatoire. Le rôle de la `entryPoint` élément dans le `vstav3` espace de noms est défini dans [ &#60;entryPoint&#62; élément &#40;développement Office dans Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md).  
  
## <a name="document-level-customization-example"></a>Exemple de personnalisation au niveau du document  
  
### <a name="description"></a>Description  
 L’exemple de code suivant illustre l’élément `entryPoints` d’un manifeste de l’application pour une solution au niveau du document déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```  
<vstav3:entryPoints>  
  <vstav3:entryPoint   
    class="ContosoExcelWorkbook.ThisWorkbook">  
    <assemblyIdentity   
      name="ContosoExcelWorkbook"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
  <vstav3:entryPoint   
    class="ContosoExcelWorkbook.Sheet1">  
    <assemblyIdentity   
      name="ContosoExcelWorkbook"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
  <vstav3:entryPoint   
    class="ContosoExcelWorkbook.Sheet2">  
    <assemblyIdentity   
      name="ContosoExcelWorkbook"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
  <vstav3:entryPoint   
    class="ContosoExcelWorkbook.Sheet3">  
    <assemblyIdentity   
      name="ContosoExcelWorkbook"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
</vstav3:entryPoints>  
```  
  
## <a name="vsto-add-in-example"></a>Exemple de complément VSTO  
  
### <a name="description"></a>Description  
 L’exemple de code suivant illustre un élément `entryPoints` d’un manifeste de l’application pour une solution au niveau de l’application déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```  
<vstav3:entryPoints>  
  <vstav3:entryPoint   
    class="ContosoOutlookAddIn.ThisAddIn">  
    <assemblyIdentity   
      name="ContosoOutlookAddIn"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
</vstav3:entryPoints>  
```  
  
## <a name="multi-project-deployment-example"></a>Exemple de déploiement de plusieurs projets  
  
### <a name="description"></a>Description  
 L’exemple de code suivant illustre l’élément `entryPoints` d’un manifeste de l’application pour un déploiement à projets multiples. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```  
<vstav3:entryPoints   
  id="ContosoExcel">  
  <vstav3:entryPoint   
    class="ContosoExcelWorkbook.ThisWorkbook">  
    <assemblyIdentity   
      name="ContosoExcelWorkbook"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
  <vstav3:entryPoint   
    class="ContosoExcelWorkbook.Sheet1">  
    <assemblyIdentity   
      name="ContosoExcelWorkbook"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
  <vstav3:entryPoint   
    class="ContosoExcelWorkbook.Sheet2">  
    <assemblyIdentity   
      name="ContosoExcelWorkbook"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
  <vstav3:entryPoint   
    class="ContosoExcelWorkbook.Sheet3">  
    <assemblyIdentity   
      name="ContosoExcelWorkbook"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
</vstav3:entryPoints>  
<vstav3:entryPoints   
  id="ContosoOutlook">  
  <vstav3:entryPoint   
    class="ContosoOutlookAddIn.ThisAddIn">  
    <assemblyIdentity   
      name="ContosoOutlookAddIn"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
</vstav3:entryPoints>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les Solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifeste d’application ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  