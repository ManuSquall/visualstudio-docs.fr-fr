---
title: "Exemple d&#39;extension Excel&#160;: classe ActionFilter | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 11
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 11
---
# Exemple d&#39;extension Excel&#160;: classe ActionFilter
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette classe interne étend la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> et représente un filtre pour les actions de tests sur un élément [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
## Propriétés simples  
 Ces propriétés en lecture seule permettent au développeur de spécifier le mode d'exécution de ce filtre d'action de test par l'infrastructure de test codé de l'interface utilisateur.  Par exemple, la propriété <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> fournit le nom du filtre d'action.  D'autres propriétés obtiennent le <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A> du filtre d'action, le <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, le nom <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> des actions filtrées par ce filtre d'action de test.  D'autres indiquent <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A> et également si l'action de test est <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>.  
  
## Méthode ProcessRule  
 Cette méthode est appelée par l'infrastructure de test codé de l'interface utilisateur et applique le filtre au <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>fourni.  Ce remplacement particulier supprime une action de clic de souris sur une cellule lorsque l'action suivante dans la pile envoie des séquences de touches à la cellule.  Il retourne alors `false`.  
  
## Méthodes privées  
 La méthode `IsLeftClick` détermine si l'action fournie représente un clic gauche de la souris.  La méthode `AreActionsOnSameExcelCell` détermine si deux actions fournies sont exécutées sur la même cellule dans Excel.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>   
 [Extension des tests codés de l'interface utilisateur t enregistrements des actions pour prendre charge Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)