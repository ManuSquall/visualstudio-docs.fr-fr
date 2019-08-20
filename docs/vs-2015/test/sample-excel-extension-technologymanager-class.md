---
title: 'Exemple d’Extension Excel : Classe TechnologyManager | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 8a7b760d-b5ac-4451-9593-6ac1a0b95cdb
caps.latest.revision: 11
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 64632c175b44a370d7dcaf48e7c0a8cee766a4ab
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68192505"
---
# <a name="sample-excel-extension-technologymanager-class"></a>Exemple d’Extension Excel : Classe TechnologyManager
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette classe étend la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>. Elle est chargée de fournir des services principaux pour l’extension [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]. Bien que la classe de base dispose de nombreuses méthodes, seule une partie d’entre elles est utilisée dans cet exemple.  
  
 Certaines méthodes retournent simplement une valeur de propriété. De nombreuses méthodes sont destinées à permettre au développeur de remplacer les algorithmes par défaut présents dans le moteur de test codé de l’interface utilisateur. Ces méthodes lèvent une exception <xref:System.NotSupportedException> ou retournent `null`, ce qui indique au framework qu’il faut utiliser l’algorithme par défaut.  
  
 Selon la complexité de la technologie sous-jacente, le développement du code du gestionnaire de technologies peut prendre de quelques semaines à quelques mois. Excel permet de créer un gestionnaire de technologies au potentiel très étendu. Cet exemple se limite volontairement aux cellules et feuilles de calcul Excel, et utilise une mise en forme restreinte.  
  
 Quand cela est possible, le code du gestionnaire de technologies utilise le canal .NET Remoting ouvert par la classe `Communicator` pour extraire les informations du complément s’exécutant dans le processus Excel.  
  
## <a name="com-visibility"></a>Visibilité COM  
 Notez que cette classe et chacune des classes d’élément qui étendent la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> ont toutes <xref:System.Runtime.InteropServices.ComVisibleAttribute> avec la valeur `true` pour s’assurer que les classes sont visibles par COM.  
  
## <a name="technologyname-property"></a>TechnologyName, propriété  
 Cette substitution de la propriété <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.TechnologyName%2A?displayProperty=fullName> doit fournir un nom unique et significatif qui identifie la technologie sous-jacente pour tous les autres composants de l’extension. Pour cette extension, la valeur est « Excel ».  
  
## <a name="getcontrolsupportlevel-method"></a>Méthode GetControlSupportLevel  
 Cette substitution de la méthode <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetControlSupportLevel%2A?displayProperty=fullName> retourne un nombre qui indique le niveau de prise en charge que le Gestionnaire de technologies peut offrir pour le contrôle représenté par le handle fourni. Plus la valeur retournée est élevée, plus le gestionnaire de technologies peut prendre en charge le contrôle. Dans ce cas, la méthode vérifie la fenêtre qui contient le contrôle. S’il s’agit d’une feuille de calcul Excel, la méthode retourne la valeur la plus élevée. Sinon, elle retourne zéro, ce qui indique qu’aucune prise en charge n’est possible.  
  
## <a name="methods-to-get-an-element"></a>Méthodes d’obtention d’un élément  
 Le framework de test codé de l’interface utilisateur dispose de plusieurs méthodes importantes pour obtenir un élément spécifique à la technologie en fournissant un handle, un point sur l’écran ou un élément d’une autre technologie. Le code de ces méthodes est explicite. Les méthodes de base sont les suivantes :  
  
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetFocusedElement%2A?displayProperty=fullName>  
  
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromPoint%2A?displayProperty=fullName>  
  
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromWindowHandle%2A?displayProperty=fullName>  
  
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromNativeElement%2A?displayProperty=fullName>  
  
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.ConvertToThisTechnology%2A?displayProperty=fullName>  
  
## <a name="parsequeryid-method"></a>ParseQueryId, méthode  
 Quand un test codé de l’interface utilisateur est créé, l’utilisateur peut spécifier des valeurs de propriété pour une partie ou l’ensemble des contrôles du test. Ces valeurs de propriété sont utilisées par le framework de test pour créer des paires nom-valeur appelées propriétés de recherche, qui permettent de rechercher des contrôles d’IU (interface utilisateur) spécifiques pendant le test. Toutes les propriétés de recherche représentent ensemble la valeur de la propriété <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A?displayProperty=fullName> de chaque élément dans la technologie, ce qui inclut chaque contrôle. Comme la recherche d’un contrôle doit parfois être effectuée plusieurs fois pendant un test, cette méthode permet au gestionnaire de technologies d’optimiser l’analyse des propriétés de recherche pour le contrôle donné. Cette méthode retourne également un cookie que le framework peut utiliser pour d’autres recherches liées à ce contrôle. Cette implémentation de la méthode utilise la méthode <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> pour analyser les propriétés de recherche.  
  
## <a name="matchelement-method"></a>MatchElement, méthode  
 Pour effectuer une recherche de contrôle par le Gestionnaire de technologies, vous pouvez implémenter la méthode <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.Search%2A?displayProperty=fullName> pour retourner un tableau de correspondances possibles, ou lever <xref:System.NotSupportedException>, qui indique au framework qu’il doit utiliser son propre algorithme de recherche. Dans les deux cas, vous devez implémenter la méthode <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.MatchElement%2A> là où cette implémentation utilise encore la méthode <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName>.  
  
## <a name="navigation-methods"></a>Méthodes de navigation  
 Ces méthodes permettent d’obtenir le parent, les enfants ou les frères de l’élément fourni dans la hiérarchie de l’IU. Le code est simple et commenté de manière claire.  
  
## <a name="getexcelelement-internal-method"></a>GetExcelElement, méthode interne  
 Cette méthode interne accepte un handle de fenêtre et les informations relatives à un élément Excel, puis retourne l’élément Excel demandé.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>   
 <xref:System.NotSupportedException>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>   
 [Extension des tests codés de l’interface utilisateur et des enregistrements des actions pour prendre charge Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
