---
title: '&lt;friendlyName&gt; élément (développement Office dans Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <friendlyName> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d038e825173f95ddfe4106022c7c9924090b3a5f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62972354"
---
# <a name="ltfriendlynamegt-element-office-development-in-visual-studio"></a>&lt;friendlyName&gt; élément (développement Office dans Visual Studio)
  L’élément `friendlyName` de l’espace de noms `vstov4` stocke le nom qui apparaît dans la liste des programmes installés.

## <a name="syntax"></a>Syntaxe

```xml
<friendlyName>
</friendlyName>
```

## <a name="elements-and-attributes"></a>Éléments et attributs
 L’élément `friendlyName` se trouve dans l’espace de noms `vstov4` . La valeur apparaît dans la liste des programmes installés sur l’ordinateur, ainsi que dans la boîte de dialogue des compléments VSTO COM des applications Microsoft Office.

 L’élément `friendlyName` n’a aucun attribut ou élément enfant.

## <a name="vsto-add-in-example"></a>Exemple de complément VSTO

### <a name="description"></a>Description
 L’exemple de code suivant illustre l’élément `friendlyName` d’une solution au niveau de l’application déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [manifestes d’Application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Code

```xml
<vstov4:friendlyName>
  ContosoOutlookAddIn
</vstov4:friendlyName>
```

## <a name="see-also"></a>Voir aussi

- [Manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)