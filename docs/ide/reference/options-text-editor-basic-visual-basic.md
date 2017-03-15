---
title: "Options, &#201;diteur de texte, De base (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Visual_Basic.Editor"
  - "VS.ToolsOptionsPages.Text_Editor.Basic.Editor"
  - "VS.ToolsOptionsPages.Visual_Basic_Editor.Editor"
  - "VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage"
  - "VS.ToolsOptionsPages.Text_Editor.Basic"
  - "VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific"
helpviewer_keywords: 
  - "Basic (boîte de dialogue Options de l'Éditeur de texte)"
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Options, &#201;diteur de texte, De base (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La page de propriétés **Spécifique à VB**, accessible via le menu **Outils**, dans la boîte de dialogue **Options**, puis dans le dossier **Éditeur de texte** et son dossier **Basic**, contient les propriétés suivantes :  
  
 **Insertion automatique de l'instruction de fin**  
 Par exemple, lorsque vous tapez la première ligne d'une déclaration de procédure, `Sub Main—`, et que vous appuyez sur ENTRÉE, l'éditeur de texte ajoute une ligne `End Sub` correspondante.  De même, si vous ajoutez une boucle [For](/dotnet/visual-basic/language-reference/statements/for-next-statement), l'éditeur de texte ajoute une instruction `Next` correspondante.  Lorsque cette option est sélectionnée, l'éditeur de code ajoute automatiquement l'instruction de fin.  
  
 **Formatage automatique avec tabulation du code**  
 L'éditeur de texte remet en forme votre code comme nécessaire.  Lorsque cette option est sélectionnée, l'éditeur de code effectue les opérations suivantes :  
  
-   aligne votre code sur la tabulation correcte,  
  
-   applique la casse correcte aux mots clés, variables et objets,  
  
-   ajoute le `Then` manquant à une instruction `If...Then`,  
  
-   ajoute des parenthèses aux appels de fonctions,  
  
-   ajoute les guillemets fermants manquants aux chaînes,  
  
-   remet en forme la notation exponentielle,  
  
-   remet en forme les dates.  
  
 **Activer le mode Plan**  
 Lorsque vous ouvrez un fichier dans l'éditeur de code, vous pouvez afficher le document en mode Plan.  Consultez [Mode Plan](../../ide/outlining.md) pour plus d'informations.  Lorsque cette option est sélectionnée, la fonctionnalité mode Plan est activée à l'ouverture d'un fichier.  
  
 **Insertion automatique des membres Interface et MustOverride**  
 Lorsque vous validez une instruction `Implements` ou `Inherits` pour une classe, l'éditeur de texte insère des prototypes pour les membres qui doivent être implémentés ou substitués, respectivement.  
  
 **Afficher les séparateurs de ligne de procédure**  
 L'éditeur de texte indique la portée visuelle des procédures.  Une ligne est dessinée dans les fichiers sources .vb de votre projet aux emplacements répertoriés dans le tableau suivant :  
  
|Emplacement dans le fichier source .vb|Exemple d'emplacement de la ligne|  
|--------------------------------------------|---------------------------------------|  
|Après la fermeture d'une construction de déclaration de bloc|-   À la fin d'une classe, d'une structure, d'un modèle, d'une interface ou d'un enum.<br />-   Après une propriété, une fonction ou un sub.<br />-   Pas entre les clauses get et set d'une propriété.|  
|Après un ensemble de constructions de lignes uniques|-   Après les instructions import, avant une définition de type dans un fichier de classe.<br />-   Après les variables déclarées dans une classe, avant toute procédure.|  
|Après les déclarations de lignes uniques \(déclaration pas au niveau des blocs\)|-   À la suite des instructions import et inherits, des déclarations de variables, des déclarations event et delegate et des instructions de déclaration de DLL.|  
  
 **Activer les suggestions de correction d'erreurs**  
 L'éditeur de texte peut suggérer des solutions aux erreurs courantes et vous permettre de sélectionner la correction appropriée, qui est appliquée ensuite à votre code.  
  
 **Activer la mise en surbrillance des références et des mots clés**  
 L'éditeur de texte peut mettre en surbrillance toutes les instances d'un symbole ou tous les mots clés dans une clause telle que `If..Then`, `While...End While` ou `Try...Catch...Finally`.  Vous pouvez naviguer entre les références ou les mots clés en surbrillance en appuyant sur CTRL\+MAJ\+FLÈCHE BAS ou CTRL\+MAJ\+FLÈCHE HAUT.  
  
## Voir aussi  
 [Général, Environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)   
 [Options, Éditeur de texte, Tous les langages, Onglets](../../ide/reference/options-text-editor-all-languages-tabs.md)