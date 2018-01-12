---
title: "&lt;formRegion&gt; élément (développement Office dans Visual Studio) | Documents Microsoft"
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
helpviewer_keywords: application manifests [Office development in Visual Studio], <formRegion> element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a0ae3645d6af740296e5b8fb9ab59add0c8579e0
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;formRegion&gt; élément (développement Office dans Visual Studio)
  L’élément `formRegion` de l’espace de noms `vstov4` identifie une zone de formulaire Microsoft Office Outlook associée à un complément VSTO.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<formRegion  
  name>  
  <messageClass  
    name/>  
</formRegion>  
```  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 L’élément `formRegion` de l’espace de noms `vstov4` identifie une zone de formulaire associée à un complément VSTO Outlook. Il est obligatoire uniquement pour les compléments VSTO Outlook qui incluent des zones de formulaire.  
  
 Plusieurs éléments `formRegion` peuvent être définis à l’intérieur d’un élément `formRegions` pour un même complément VSTO.  
  
 L’élément `formRegion` comporte l’attribut suivant.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`name`|Obligatoire. Identifie le nom de la zone de formulaire.|  
  
 L’élément `formRegion` comporte les éléments enfants suivants.  
  
### <a name="messageclass"></a>messageClass  
 L’élément `messageClass` identifie le formulaire Outlook associé à la zone de formulaire.  
  
 L’élément `messageClass` comporte l’attribut suivant.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`name`|Obligatoire. Identifie le formulaire associé à la zone de formulaire.|  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre un élément `formRegion` dans le manifeste d’application d’un complément VSTO Outlook déployé à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cette zone de formulaire est associée à trois classes de message. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<vstov4:formRegion  
    name="OutlookAddIn1.FormRegion1">  
  <vstov4:messageClass name="IPM.Note" />  
  <vstov4:messageClass name="IPM.Contact" />  
  <vstov4:messageClass name="IPM.Appointment" />  
</vstov4:formRegion>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Création de zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)   
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les Solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifeste d’application ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  