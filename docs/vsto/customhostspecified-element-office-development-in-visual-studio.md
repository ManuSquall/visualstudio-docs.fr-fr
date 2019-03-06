---
title: '&lt;customHostSpecified&gt; élément (développement Office dans Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 26597796c99d3ab8740812819cf3aa5568e2985b
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874378"
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;customHostSpecified&gt; élément (développement Office dans Visual Studio)
  Le `customHostSpecified` élément indique que cette solution n’est pas une application autonome. Les solutions Office contiennent des composants qui sont hébergés au sein des applications Microsoft Office.

## <a name="syntax"></a>Syntaxe

```xml
<customHostSpecified />
```

## <a name="elements-and-attributes"></a>Éléments et attributs
 Le `customHostSpecified` élément est requis pour les solutions Office. Cet élément est dans le `co.v1` espace de noms et spécifie que ce déploiement contient un composant qui sera déployé sur un hôte personnalisé et n’est pas une application autonome.

 Cet élément est un enfant du premier `<entrypoint>` élément dans le manifeste d’application. Il ne peut y avoir aucun autre élément enfant qui `<entrypoint>` élément ou [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] déclenchera une erreur de validation pendant l’installation.

 Cet élément possède pas d’attributs et pas d’éléments enfants.

## <a name="example"></a>Exemple
 L’exemple de code suivant illustre la `customHostSpecified` élément dans un manifeste d’application pour une solution Office. Cet exemple de code fait partie d’un exemple plus complet fourni dans [manifestes d’Application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

## <a name="see-also"></a>Voir aussi

- [Manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)