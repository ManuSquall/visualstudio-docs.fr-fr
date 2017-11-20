---
title: "&lt;appAddin&gt; élément (développement Office dans Visual Studio) | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: application manifests [Office development in Visual Studio], <appAddin> element
ms.assetid: 6152fe5b-6af1-465d-aee7-19e4fd4d04c1
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c5637a449ea40f6e4f910e061c7e2e324c91ae70
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;appAddin&gt; élément (développement Office dans Visual Studio)
  L’élément `appAddin` de l’espace de noms `vstov4` stocke les informations propres à la personnalisation des compléments VSTO.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<appAddin  
  application  
  loadBehavior  
  keyName>  
  <friendlyName>  
  <description>  
  <formRegions></formRegions>  
</appAddin>  
```  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 L’élément `appAddin` est obligatoire et se trouve dans l’espace de noms `vstov4` . Il existe un seul élément `appAddin` défini dans un manifeste de l’application.  
  
 L’élément `appAddin` a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`application`|Obligatoire. Identifie l’application Microsoft Office. La valeur peut être l’une des suivantes : Excel, InfoPath, Outlook, PowerPoint, Project, Visio ou Word.|  
|`loadBehavior`|Facultatif. Par défaut, `loadBehavior` est activé en définissant cette valeur sur . Pour le débogage, vous pouvez désactiver le complément VSTO en définissant la valeur sur deux. Pour plus d’informations, consultez le tableau intitulé Valeurs LoadBehavior dans [Registry Entries for VSTO Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).|  
|`keyName`|Obligatoire. Cette valeur est le nom de la clé de Registre que l’application utilise pour charger le complément VSTO. Pour plus d'informations, consultez [Registry Entries for VSTO Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).|  
  
 L’élément `appAddin` possède les éléments enfants suivants.  
  
### <a name="friendlyname"></a>FriendlyName  
 Facultatif. Le `friendlyName` élément est expliqué dans [&#60; friendlyName &#62; Élément &#40; développement Office dans Visual Studio &#41; ](../vsto/friendlyname-element-office-development-in-visual-studio.md).  
  
### <a name="description"></a>Description  
 Facultatif. Le `description` élément est expliqué dans [&#60; description &#62; Élément &#40; développement Office dans Visual Studio &#41; ](../vsto/description-element-office-development-in-visual-studio.md).  
  
### <a name="formregions"></a>formRegions  
 Obligatoire uniquement pour les compléments VSTO Outlook qui comprennent des zones de formulaire. Le `formRegions` élément est expliqué dans [&#60; formRegions &#62; Élément &#40; développement Office dans Visual Studio &#41; ](../vsto/formregions-element-office-development-in-visual-studio.md).  
  
## <a name="vsto-add-in-example"></a>Exemple de complément VSTO  
  
### <a name="description"></a>Description  
 L’exemple de code suivant illustre les éléments `appAddin` dans une solution Outlook déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```  
<vstov4:appAddIn   
  application="Outlook"   
  loadBehavior="3"   
  keyName="ContosoOutlookAddIn">  
  <vstov4:friendlyName>  
    ContosoOutlookAddIn  
  </vstov4:friendlyName>  
  <vstov4:description>  
    ContosoOutlookAddIn - Outlook VSTO Add-in   
    created with Visual Studio Tools for Office  
  </vstov4:description>  
  <vstov4:formRegions>  
    <vstov4:formRegion  
        name="OutlookAddIn1.FormRegion1">  
      <vstov4:messageClass name="IPM.Note" />  
      <vstov4:messageClass name="IPM.Contact" />  
      <vstov4:messageClass name="IPM.Appointment" />  
    </vstov4:formRegion>  
  </vstov4:formRegions>  
</vstov4:appAddIn>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les Solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifeste d’application ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  