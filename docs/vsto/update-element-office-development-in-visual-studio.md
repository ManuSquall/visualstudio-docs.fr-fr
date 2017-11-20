---
title: "&lt;mettre à jour&gt; élément (développement Office dans Visual Studio) | Documents Microsoft"
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
helpviewer_keywords:
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
ms.assetid: bdd5dbf7-ddda-4ef6-9db5-1fb4405261a0
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3a41e7580e7c6c169554bb50c4d0c9af29a992b5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;mettre à jour&gt; élément (développement Office dans Visual Studio)
  Le `update` élément spécifie la fréquence à laquelle la solution recherchera les mises à jour.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<update  
  enabled>  
  <expiration  
    maximumAge  
    unit  
  />  
</update>  
```  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 L’élément `update` est obligatoire et se trouve dans l’espace de noms `vstav3`.  
  
 Le `update` élément a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Obligatoire. Définissez activé à une des valeurs suivantes :<br /><br /> -   **true** pour rechercher les mises à jour.<br />-   **false** pour empêcher la vérification des mises à jour.|  
  
 Le `update` élément possède les éléments enfants suivants.  
  
### <a name="expiration"></a>expiration  
 L’élément `expiration` est obligatoire et se trouve dans l’espace de noms `vstav3`. Cet élément spécifie l’intervalle auquel la solution vérifie les mises à jour.  
  
 Le `expiration` élément a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`maximumAge`|-Requis. Valeur égale à un entier.|  
|`unit`|Obligatoire. Définissez `unit` à une des valeurs suivantes :<br /><br /> -   **heures**<br />-   **jours d’utilisation**<br />-   **semaines**|  
  
## <a name="example-of-always-checking-for-updates"></a>Exemple de recherche toujours les mises à jour  
  
### <a name="description"></a>Description  
 L’exemple de code suivant illustre un `update` élément qui est défini sur toujours vérifier les mises à jour dans les solutions Office.  
  
### <a name="code"></a>Code  
  
```  
<vstav3:update enabled="true" />  
```  
  
## <a name="example-of-setting-a-default-update-interval"></a>Exemple de définition d’un intervalle de mise à jour par défaut  
  
### <a name="description"></a>Description  
 L’exemple de code suivant illustre un `update` élément dans un manifeste d’application pour les solutions Office. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```  
<vstav3:update enabled="true">  
    <vstav3:expiration maximumAge="7" unit="days" />  
</vstav3:update>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’une Solution Office à l’aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les Solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifeste d’application ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  