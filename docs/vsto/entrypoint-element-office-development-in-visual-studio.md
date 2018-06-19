---
title: '&lt;point d’entrée&gt; élément (développement Office dans Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <entryPoint> element
- <entryPoint> element
- entryPoint element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6eb617b44eb5360ea8c313431c7d8609505efa16
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34447087"
---
# <a name="ltentrypointgt-element-office-development-in-visual-studio"></a>&lt;point d’entrée&gt; élément (développement Office dans Visual Studio)
  Chaque élément `entryPoint` de l’espace de noms `vstav3` identifie un assembly de personnalisation qui doit être exécuté lorsque cette application [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] est installée.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<entryPoint class>  
    <assemblyIdentity />  
</entryPoint>  
```  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 L’élément `entryPoint` est obligatoire et se trouve dans l’espace de noms `vstav3` .  
  
 Chaque élément `entryPoint` peut contenir un seul assembly de personnalisation. Plusieurs éléments `entryPoint` peuvent être définis dans un manifeste d’application.  
  
 L’élément `entryPoint` a les attributs suivants :  
  
|Attribut|Description|  
|---------------|-----------------|  
|`class`|Obligatoire. Identifie un assembly de personnalisation à exécuter. La syntaxe de cet attribut est *NomEspaceNoms.NomClasse*.|  
  
 `entryPoint` possède l’élément suivant.  
  
### <a name="assemblyidentity"></a>assemblyIdentity  
 Obligatoire. L’élément `assemblyIdentity` de l’espace de noms `vstav3` fait référence à un élément `assemblyIdentity` du manifeste d’application [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .  
  
 Le rôle de `assemblyIdentity` et ses attributs est défini dans [ &#60;assemblyIdentity&#62; élément &#40;application ClickOnce&#41;](/visualstudio/deployment/assemblyidentity-element-clickonce-application).  
  
## <a name="document-level-customization-example"></a>Exemple de personnalisation au niveau du document  
  
### <a name="description"></a>Description  
 L’exemple de code suivant illustre les éléments `entryPoint` d’un manifeste d’application pour une solution Office au niveau du document déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [manifestes d’Application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```xml  
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
```  
  
## <a name="vsto-add-in-example"></a>Exemple de complément VSTO  
  
### <a name="description"></a>Description  
 L’exemple de code suivant illustre un élément `entryPoint` d’un manifeste d’application pour une solution Office au niveau de l’application déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [manifestes d’Application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```xml
<vstav3:entryPoint   
  class="ContosoOutlookAddIn.ThisAddIn">  
  <assemblyIdentity   
    name="ContosoOutlookAddIn"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifeste d’application ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  