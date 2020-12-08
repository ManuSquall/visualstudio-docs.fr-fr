---
title: '&lt;description &gt; , élément (développement Office dans Visual Studio)'
description: Découvrez que l’élément Description de l’espace de noms vstov4 stocke la description de la solution Office qui s’affiche dans la boîte de dialogue Compléments COM.
titleSuffix: ''
ms.custom: secdec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 377599e770a93faca9e283ec543091508b773bc7
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846231"
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;description &gt; , élément (développement Office dans Visual Studio)
  L’élément `description` de l’espace de noms `vstov4` stocke la description de la solution Office qui s’affiche dans la boîte de dialogue des compléments COM des applications Microsoft Office.

## <a name="syntax"></a>Syntaxe

```xml
<description>
</description>
```

## <a name="elements-and-attributes"></a>Éléments et attributs
 facultatif. L’élément `description` se trouve dans l’espace de noms `vstov4` . Il contient la description du complément qui s’affiche dans la boîte de dialogue des compléments COM des applications Microsoft Office.

 L’élément `description` n’a aucun attribut ou élément.

## <a name="vsto-add-in-example"></a>Exemple de complément VSTO

### <a name="description"></a>Description
 L’exemple de code suivant illustre l’élément `description` d’une solution au niveau de l’application déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [les manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Code

```xml
<vstov4:description>
  ContosoOutlookAddIn - Outlook add-in
  created with Visual Studio Tools for Office
</vstov4:description>
```

## <a name="see-also"></a>Voir aussi

- [Manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)