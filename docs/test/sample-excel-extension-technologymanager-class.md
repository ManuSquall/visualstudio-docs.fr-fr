---
title: "Exemple d&#39;extension Excel&#160;: classe TechnologyManager | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8a7b760d-b5ac-4451-9593-6ac1a0b95cdb
caps.latest.revision: 9
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 9
---
# Exemple d&#39;extension Excel&#160;: classe TechnologyManager
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette classe étend la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> et est chargée de fournir des services principaux pour l'extension [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  Bien que la classe de base comporte de nombreuses méthodes, seul un sous\-ensemble est utilisé dans cet exemple.  
  
 Certaines méthodes retournent juste une valeur de propriété.  De nombreuses méthodes visent à autoriser le développeur à remplacer la génération d'algorithmes par défaut dans le moteur des tests codés de l'interface utilisateur.  Ces méthodes lèvent une <xref:System.NotSupportedException> ou retournent `null`, qui indique à l'infrastructure d'utiliser l'algorithme par défaut.  
  
 En fonction de la complexité de la technologie sous\-jacente, le développement du code du gestionnaire de technologies pourrait prendre entre quelques semaines et quelques mois.  Excel offre une possibilité de créer un gestionnaire de technologies potentiellement très complète.  Cet exemple est limité volontairement aux feuilles de calcul et cellules Excel et utilise une mise en forme limitée.  
  
 Si possible, le code du gestionnaire de technologies utilise le canal .NET Remoting ouvert par la classe `Communicator` pour extraire des informations du complément en cours d'exécution dans le processus Excel.  
  
## Visibilité COM  
 Notez que cette classe et chacune des classes d'éléments qui étendent la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> possèdent l'<xref:System.Runtime.InteropServices.ComVisibleAttribute> avec la valeur `true` pour s'assurer que les classes sont visibles par COM.  
  
## Propriété TechnologyName  
 Le remplacement de la propriété <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.TechnologyName%2A?displayProperty=fullName> doit fournir un nom unique et significatif qui identifie la technologie sous\-jacente pour chaque autre composant de l'extension.  Pour cette extension, la valeur est « Excel ».  
  
## Méthode GetControlSupportLevel  
 Ce remplacement de la méthode <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetControlSupportLevel%2A?displayProperty=fullName> retourne un nombre qui indique le niveau de prise en charge que le gestionnaire de technologies peut offrir pour le contrôle représenté par le handle fourni.  Plus la valeur retournée est élevée, plus le gestionnaire de technologies peut prendre en charge le contrôle.  Dans ce cas, la méthode vérifie la fenêtre qui contient le contrôle et, s'il s'agit d'une feuille de calcul Excel, la méthode retourne la valeur la plus élevée ; sinon, il retourne zéro, ce qui indique qu'aucune prise en charge n'est assurée.  
  
## Méthodes pour obtenir un élément  
 Il existe plusieurs méthodes importantes utilisées par l'infrastructure de test codé de l'interface utilisateur pour obtenir un élément spécifique à la technologie en fournissant un handle, un point sur l'écran ou un élément d'une technologie différente.  Le code pour ces méthodes est évident.  Les méthodes de base sont les suivantes :  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetFocusedElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromPoint%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromWindowHandle%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromNativeElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.ConvertToThisTechnology%2A?displayProperty=fullName>  
  
## Méthode ParseQueryId  
 Lorsqu'un test codé de l'interface utilisateur est créé, l'utilisateur peut spécifier des valeurs de propriété pour tout ou partie des contrôles dans le test.  Ces valeurs de propriété sont utilisées par l'infrastructure de test pour créer des paires nom\-valeur appelées propriétés de recherche et qui sont utilisées pour rechercher des contrôles d'interface utilisateur spécifiques pendant le test.  Toutes les propriétés de recherche représentent ensemble la valeur de la propriété <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A?displayProperty=fullName> de chaque élément dans la technologie, qui inclut chaque contrôle.  Comme un contrôle peut être trouvé plusieurs fois au cours d'un test, cette méthode permet au gestionnaire de technologies d'optimiser l'analyse des propriétés de recherche pour le contrôle donné.  Cette méthode retourne également un cookie que l'infrastructure peut utiliser pour les recherches suivantes de ce contrôle.  Cette implémentation de la méthode utilise la méthode <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> pour analyser les propriétés de recherche.  
  
## Méthode MatchElement  
 Pour exécuter une recherche des contrôles par le gestionnaire de technologies, vous pouvez implémenter la méthode <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.Search%2A?displayProperty=fullName> pour retourner ou un tableau de correspondances possibles ou pour lever l' <xref:System.NotSupportedException>, qui indique à l'infrastructure d'utiliser son propre algorithme de recherche.  Dans les deux cas, vous devez implémenter la méthode <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.MatchElement%2A> dans laquelle cette implémentation utilise encore la méthode <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName>.  
  
## Méthodes de navigation  
 Ces méthodes obtiennent le parent, les enfants ou les frères de l'élément fourni de la hiérarchie d'IU.  Le code est simple et commenté clairement.  
  
## Méthode interne GetExcelElement  
 Cette méthode interne prend un handle de fenêtre et des informations sur un élément Excel et retourne l'élément Excel demandé.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>   
 <xref:System.NotSupportedException>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>   
 [Extension des tests codés de l'interface utilisateur t enregistrements des actions pour prendre charge Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)