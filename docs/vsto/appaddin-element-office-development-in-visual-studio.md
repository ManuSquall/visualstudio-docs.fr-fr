---
title: '&lt;appAddin&gt; élément (développement Office dans Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <appAddin> element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 572de1a3fccf9b66000d82e14f7895ab5cf0029f
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304869"
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;appAddin&gt; élément (développement Office dans Visual Studio)
  Le **appAddin** élément de la `vstov4` espace de noms stocke des informations spécifiques à la personnalisation des Compléments VSTO.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml 
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
 Le **appAddin** élément est obligatoire et se trouve dans le `vstov4` espace de noms. Il existe un seul **appAddin** élément défini dans un manifeste d’application.  
  
 Le **appAddin** élément a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|**Application**|Obligatoire. Identifie l’application Microsoft Office. La valeur peut être l’une des suivantes : Excel, InfoPath, Outlook, PowerPoint, Project, Visio ou Word.|  
|**LoadBehavior**|Facultatif. Par défaut, le **loadBehavior** est activé en définissant cette valeur sur. Pour le débogage, vous pouvez désactiver le complément VSTO en définissant la valeur sur deux. Pour plus d’informations, consultez le tableau intitulé valeurs LoadBehavior dans [les entrées de Registre pour les Compléments VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|  
|**keyName**|Obligatoire. Cette valeur est le nom de la clé de Registre que l’application utilise pour charger le complément VSTO. Pour plus d’informations, consultez [les entrées de Registre pour les Compléments VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|  
  
 Le **appAddin** élément possède les éléments enfants suivants.  
  
### <a name="friendlyname"></a>FriendlyName  
 Facultatif. Le **friendlyName** élément est expliqué dans [ &#60;friendlyName&#62; élément &#40;développement Office dans Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md).  
  
### <a name="description"></a>Description  
 Facultatif. Le **description** élément est expliqué dans [ &#60;description&#62; élément &#40;développement Office dans Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md).  
  
### <a name="formregions"></a>formRegions  
 Obligatoire uniquement pour les compléments VSTO Outlook qui comprennent des zones de formulaire. Le **formRegions** élément est expliqué dans [ &#60;formRegions&#62; élément &#40;développement Office dans Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md).  
  
## <a name="vsto-add-in-example"></a>Exemple de complément VSTO  
  
### <a name="description"></a>Description  
 L’exemple de code suivant illustre **appAddin** éléments dans une solution Outlook déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [manifestes d’Application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```xml  
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
 [Manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifeste d’application ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  