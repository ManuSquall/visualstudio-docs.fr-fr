---
title: "&lt;update&gt;, &#233;l&#233;ment (d&#233;veloppement Office dans Visual Studio)"
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
  - "update (élément)"
  - "<update> (élément)"
  - "manifestes d’application (développement Office dans Visual Studio), élément <update>"
ms.assetid: bdd5dbf7-ddda-4ef6-9db5-1fb4405261a0
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# &lt;update&gt;, &#233;l&#233;ment (d&#233;veloppement Office dans Visual Studio)
  L'élément `update` spécifie la fréquence selon laquelle la solution recherchera des mises à jour.  
  
## Syntaxe  
  
```  
<update  
  enabled>  
  <expiration  
    maximumAge  
    unit  
  />  
</update>  
```  
  
## Éléments et attributs  
 L'élément `update` est obligatoire et se trouve dans l'espace de noms `vstav3`.  
  
 L'élément `update` a les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`enabled`|Obligatoire.  Activez \(enabled\) l'une des valeurs suivantes :<br /><br /> -   **true** pour rechercher des mises à jour.<br />-   **false** empêcher la recherche de mises à jour.|  
  
 L'élément `update` contient les éléments enfants suivants.  
  
### expiration  
 L'élément `expiration` est obligatoire et se trouve dans l'espace de noms `vstav3`.  Cet élément  spécifie la fréquence selon laquelle la solution recherche des mises à jour.  
  
 L'élément `expiration` a les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`maximumAge`|-   Obligatoire.  Affectez un entier à cet élément.|  
|`unit`|Obligatoire.  Affectez la valeur `unit` à l'une des valeurs suivantes :<br /><br /> -   **heures**<br />-   **jours**<br />-   **semaines**|  
  
## Exemple de recherche systématique de mises à jour  
  
### Description  
 L'exemple de code suivant illustre un élément `update` configuré pour toujours rechercher les mises à jour dans les solutions Office.  
  
### Code  
  
```  
<vstav3:update enabled="true" />  
```  
  
## Exemple de définition d'une fréquence de mise à jour par défaut  
  
### Description  
 L'exemple de code suivant illustre un élément `update` dans un manifeste d'application pour les solutions Office.  Cet exemple de code fait partie d'un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:update enabled="true">  
    <vstav3:expiration maximumAge="7" unit="days" />  
</vstav3:update>  
```  
  
## Voir aussi  
 [Déploiement d'une solution Office à l'aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  