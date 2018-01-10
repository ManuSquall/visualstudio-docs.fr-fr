---
title: "Exemple d’extension Excel : classe ActionFilter | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 8f2aa063163898a87ff563a356f6bb389cb07243
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2018
---
# <a name="sample-excel-extension-actionfilter-class"></a>Exemple d'extension Excel : classe ActionFilter
Cette classe interne étend la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> et représente un filtre pour les actions de test sur un élément [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
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
