---
title: Options, Éditeur de texte, Basic (VB), Avancé
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Visual_Basic.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.Editor
- VS.ToolsOptionsPages.Visual_Basic_Editor.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage
- VS.ToolsOptionsPages.Text_Editor.Basic
- VS.ToolsOptionsPages.Text_Editor.Basic.Advanced
- VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific
helpviewer_keywords:
- Basic Text Editor Options dialog box
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6ca2178b61aa3cd2aa83314f00c231d564a10944
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53871237"
---
# <a name="options-text-editor-basic-visual-basic-advanced"></a>Option, Éditeur de texte, Basic (Visual Basic), Avancé
La page de propriétés **Spécifique à VB**, accessible via le menu **Outils**, dans la boîte de dialogue **Options**, puis dans le dossier **Éditeur de texte** et son dossier **De base**, contient les propriétés suivantes :

 **Activer la mise en surbrillance des références et des mots clés**

L’éditeur de texte peut mettre en surbrillance toutes les instances d’un symbole ou tous les mots clés dans une clause, par exemple `If..Then`, `While...End While` ou `Try...Catch...Finally`. Vous pouvez naviguer entre les références ou les mots clés surlignés en appuyant sur **Ctrl** + **Maj** + **Flèche vers le bas** ou **Ctrl** + **Maj** + **Flèche vers le haut**.

**Activer le mode Plan**

Quand vous ouvrez un fichier dans l’éditeur de code, vous pouvez afficher le document en mode Plan. Pour plus d’informations, consultez [Mode Plan](../../ide/outlining.md). Quand cette option est sélectionnée, la fonctionnalité mode Plan est activée à l’ouverture d’un fichier.

**Afficher les séparateurs de ligne de procédure**

L’éditeur de texte indique la portée visuelle des procédures. Une ligne est tracée dans les fichiers sources *.vb* de votre projet, aux emplacements présentés dans le tableau suivant :

|Emplacement dans le fichier source .vb|Exemple d’emplacement de la ligne|
|---------------------------------|------------------------------|
|Après la fermeture d’une construction de déclaration de bloc|-   À la fin d’une classe, d’une structure, d’un module, d’une interface ou d’un enum<br />-   Après une propriété, une fonction ou un sub<br />-   Pas entre les clauses get et set d’une propriété|
|Après un ensemble de constructions de lignes uniques|-   Après les instructions import, avant une définition de type dans un fichier de classe<br />-   Après les variables déclarées dans une classe, avant toute procédure|
|Après les déclarations de lignes uniques (déclarations pas au niveau des blocs)|-   À la suite des instructions import et inherits, des déclarations de variables, des déclarations event et delegate, et des instructions declare de DLL|

 **Listing en mode Pretty (remise en forme) du code** L’éditeur de texte remet en forme votre code comme il convient. Quand cette option est sélectionnée, l’éditeur de code effectue les opérations suivantes :

-   Aligner votre code sur la tabulation correcte

-   Appliquer la casse correcte aux mots clés, variables et objets

-   Ajouter un élément `Then` manquant à une instruction `If...Then`

-   Ajouter des parenthèses aux appels de fonctions

-   Ajouter les guillemets fermants manquants aux chaînes

-   Remettre en forme la notation exponentielle

-   Remettre en forme les dates

**Insertion automatique des constructions de fin**

 Par exemple, quand vous tapez la première ligne d’une déclaration de procédure, `Sub Main—`, et que vous appuyez sur **Entrée**, l’éditeur de texte ajoute une ligne `End Sub` correspondante. De même, si vous ajoutez une boucle [For](/dotnet/visual-basic/language-reference/statements/for-next-statement), l’éditeur de texte ajoute une instruction `Next` correspondante. Quand cette option est sélectionnée, l’éditeur de code ajoute automatiquement la construction de fin.

**Insertion automatique des membres Interface et MustOverride**

Quand vous validez une instruction `Implements` ou `Inherits` pour une classe, l’éditeur de texte insère des prototypes pour les membres qui doivent être implémentés ou substitués, respectivement.

**Activer les suggestions de correction d’erreurs**

L’éditeur de texte peut suggérer des solutions aux erreurs courantes et vous permettre de sélectionner la correction appropriée, qui est appliquée ensuite à votre code.

## <a name="see-also"></a>Voir aussi

- [Général, Environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)
- [Options, Éditeur de texte, Tous les langages, Onglets](../../ide/reference/options-text-editor-all-languages-tabs.md)