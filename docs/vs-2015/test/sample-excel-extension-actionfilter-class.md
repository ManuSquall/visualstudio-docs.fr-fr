---
title: 'Exemple d’extension Excel : classe ActionFilter | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4c286f25159f3ee1934a27d2242e97482f7ec424
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672182"
---
# <a name="sample-excel-extension-actionfilter-class"></a>Exemple d'extension Excel : classe ActionFilter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette classe interne étend la classe [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)) et représente un filtre pour les actions de test sur un élément [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].

## <a name="simple-properties"></a>Propriétés simples
 Ces propriétés en lecture seule permettent au développeur de spécifier comment ce filtre d’action de test doit être exécuté par le framework de test codé de l’interface utilisateur. Par exemple, la propriété `UITestActionFilter.Name` fournit le nom du filtre d’action. D’autres propriétés obtiennent le `UITestActionFilter.Category` du filtre d’action, le `UITestActionFilter.FilterType` et le nom `UITestActionFilter.Group` pour les actions de test qui sont filtrées par ce filtre d’action de test. D’autres indiquent s’il faut `UITestActionFilter.ApplyTimeout` et également si l’action de test est `UITestActionFilter.Enabled`.

## <a name="processrule-method"></a>ProcessRule, méthode
 Cette méthode est appelée par le framework de test codé de l’interface utilisateur et exécute le filtre sur le `IUITestActionStack` fourni. Cette substitution particulière supprime une action permettant de choisir une cellule avec la souris quand l’action suivante de la pile envoie des séquences de touches à la cellule. Elle retourne ensuite `false`.

## <a name="private-methods"></a>Méthodes privées
 La méthode `IsLeftClick` détermine si l’action fournie représente un clic gauche de souris. La méthode `AreActionsOnSameExcelCell` détermine si deux actions fournies sont exécutées sur la même cellule dans Excel.

## <a name="see-also"></a>Voir aussi

- [Extension des tests codés de l’interface utilisateur et des enregistrements des actions pour prendre charge Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
