---
title: "Exemple d&#39;extension Excel&#160;: classe PropertyProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 075d9b8d-8658-4fca-8711-08304dbac1c5
caps.latest.revision: 9
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 9
---
# Exemple d&#39;extension Excel&#160;: classe PropertyProvider
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette classe interne étend la classe <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> et fournit des services de propriété pour les éléments [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] afin d'enregistrer et d'effectuer la lecture des tests de l'interface utilisateur.  
  
## Méthode GetControlSupportLevel  
 La méthode <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A> retourne un nombre qui indique le niveau de support que le fournisseur de propriétés peut offrir pour le contrôle fourni.  Plus la valeur retournée est élevée, plus le fournisseur de propriétés peut prendre en charge le contrôle.  Dans ce cas, la méthode vérifie la valeur de la propriété <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A> du contrôle fourni.  Si la valeur est « Excel » et si le <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> indique qu'il s'agit d'un `CellElement`, la méthode retourne la valeur la plus élevée ; sinon, il retourne zéro, ce qui indique qu'aucun support n'est fourni.  
  
## Méthode GetPropertyNames  
 Retourne un dictionnaire de noms de propriété et des descripteurs de propriété pour les propriétés prises en charge d'un contrôle de cellule Excel.  
  
## Méthode GetPropertyDescriptor  
 Cette méthode est appelée par l'infrastructure de test pour recevoir le descripteur de propriété prédéfini pour le nom de la propriété fourni.  
  
## Méthodes GetPropertyValue et SetPropertyValue  
 La méthode `GetPropertyValue` utilise la classe `Communicator` de cette extension pour retourner la valeur de propriété d'Excel.  La méthode `SetPropertyValue` utilise la classe <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> et le composant `Communicator` pour définir la valeur de propriété.  Ces méthodes sont appelées par l'infrastructure de test.  
  
## Méthodes de personnalisation de la génération de code  
 Ces méthodes ne sont pas implémentées pour cette extension.  Par conséquent, ils retournent `null` ou lèvent l'exception <xref:System.NotImplementedException>.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>   
 [Extension des tests codés de l'interface utilisateur t enregistrements des actions pour prendre charge Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)