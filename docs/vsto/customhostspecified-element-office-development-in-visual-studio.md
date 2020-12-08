---
title: '&lt;&gt;élément customHostSpecified (développement Office dans Visual Studio)'
description: Découvrez comment l’élément customHostSpecified indique que cette solution n’est pas une application autonome.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e8327c6e154f051f5ce79d41ceaa696e330c794f
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848129"
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;&gt;élément customHostSpecified (développement Office dans Visual Studio)
  L' `customHostSpecified` élément indique que cette solution n’est pas une application autonome. Les solutions Office contiennent des composants qui sont hébergés dans des applications Microsoft Office.

## <a name="syntax"></a>Syntaxe

```xml
<customHostSpecified />
```

## <a name="elements-and-attributes"></a>Éléments et attributs
 L' `customHostSpecified` élément est requis pour les solutions Office. Cet élément se trouve dans l' `co.v1` espace de noms et spécifie que ce déploiement contient un composant qui sera déployé au sein d’un hôte personnalisé et qui n’est pas une application autonome.

 Cet élément est un enfant du premier `<entrypoint>` élément du manifeste de l’application. Cet élément ne peut pas contenir d’autres éléments enfants `<entrypoint>` ou [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] déclenchera une erreur de validation lors de l’installation.

 Cet élément n’a pas d’attributs ni d’éléments enfants.

## <a name="example"></a> Exemple
 L’exemple de code suivant illustre l' `customHostSpecified` élément d’un manifeste d’application pour une solution Office. Cet exemple de code fait partie d’un exemple plus complet fourni dans [les manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

## <a name="see-also"></a>Voir aussi

- [Manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)