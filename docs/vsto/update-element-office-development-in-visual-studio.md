---
title: '&lt;Update &gt; , élément (développement Office dans Visual Studio)'
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 241bddb8c79a01bb1ba6921486a4dc46d99940cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537382"
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;Update &gt; , élément (développement Office dans Visual Studio)
  L' `update` élément spécifie l’intervalle auquel la solution recherchera les mises à jour.

## <a name="syntax"></a>Syntaxe

```xml
<update
  enabled>
  <expiration
    maximumAge
    unit
  />
</update>
```

## <a name="elements-and-attributes"></a>Éléments et attributs
 L’élément `update` est obligatoire et se trouve dans l’espace de noms `vstav3` .

 L’élément `update` a les attributs suivants.

|Attribut|Description|
|---------------|-----------------|
|`enabled`|Obligatoire. Définissez Enabled sur l’une des valeurs suivantes :<br /><br /> -   **true** pour rechercher les mises à jour.<br />-   **false** pour empêcher la vérification des mises à jour.|

 L’élément `update` comporte les éléments enfants suivants.

### <a name="expiration"></a>expiration
 L’élément `expiration` est obligatoire et se trouve dans l’espace de noms `vstav3` . Cet élément spécifie l’intervalle auquel la solution recherche les mises à jour.

 L’élément `expiration` a les attributs suivants.

|Attribut|Description|
|---------------|-----------------|
|`maximumAge`| Obligatoire. Affectez-lui une valeur entière.|
|`unit`|Obligatoire. Définissez l' `unit` une des valeurs suivantes :<br /><br /> -   **travaillé**<br />-   **précédant**<br />-   **semaines**|

## <a name="example-of-always-checking-for-updates"></a>Exemple de recherche systématique des mises à jour

### <a name="description"></a>Description
 L’exemple de code suivant illustre un `update` élément qui est défini pour toujours rechercher les mises à jour dans les solutions Office.

### <a name="code"></a>Code

```xml
<vstav3:update enabled="true" />
```

## <a name="example-of-setting-a-default-update-interval"></a>Exemple de définition d’un intervalle de mise à jour par défaut

### <a name="description"></a>Description
 L’exemple de code suivant illustre un `update` élément dans un manifeste d’application pour les solutions Office. Cet exemple de code fait partie d’un exemple plus complet fourni dans [les manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Code

```xml
<vstav3:update enabled="true">
    <vstav3:expiration maximumAge="7" unit="days" />
</vstav3:update>
```

## <a name="see-also"></a>Voir aussi

- [Déployer une solution Office à l’aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)
