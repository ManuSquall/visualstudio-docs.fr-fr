---
title: 'Exemple d’Extension Excel : Classe ActionFilter | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 13
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 86c1dda46ed0e62649a576a12c9f9e48561ec891
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54767842"
---
# <a name="sample-excel-extension-actionfilter-class"></a>Exemple d’Extension Excel : Classe ActionFilter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette classe interne étend la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> et représente un filtre pour les actions de test sur un élément [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].  
  
## <a name="simple-properties"></a>Propriétés simples  
 Ces propriétés en lecture seule permettent au développeur de spécifier comment ce filtre d’action de test doit être exécuté par le framework de test codé de l’interface utilisateur. Par exemple, la propriété <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> fournit le nom du filtre d’action. D’autres propriétés obtiennent le <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A> du filtre d’action, le <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A> et le nom <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> pour les actions de test qui sont filtrées par ce filtre d’action de test. D’autres indiquent s’il faut <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A> et également si l’action de test est <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>.  
  
## <a name="processrule-method"></a>ProcessRule, méthode  
 Cette méthode est appelée par le framework de test codé de l’interface utilisateur et exécute le filtre sur le <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack> fourni. Cette substitution particulière supprime une action permettant de choisir une cellule avec la souris quand l’action suivante de la pile envoie des séquences de touches à la cellule. Elle retourne ensuite `false`.  
  
## <a name="private-methods"></a>Méthodes privées  
 La méthode `IsLeftClick` détermine si l’action fournie représente un clic gauche de souris. La méthode `AreActionsOnSameExcelCell` détermine si deux actions fournies sont exécutées sur la même cellule dans Excel.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>   
 [Extension des tests codés de l’interface utilisateur et des enregistrements des actions pour prendre charge Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
