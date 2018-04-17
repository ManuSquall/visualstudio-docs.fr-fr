---
title: '&lt;mettre à jour&gt; élément (développement Office dans Visual Studio) | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2f0e1fdc26e285ce9b6a1fd5ecc1aa638fe909b8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
|`unit`|Obligatoire. Définissez `unit` à une des valeurs suivantes :<br /><br /> -   **Heures**<br />-   **Jours d’utilisation**<br />-   **Semaines**|  
  
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
  
  