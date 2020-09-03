---
title: Options, Éditeur de texte, Tous les langages
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.ResJSON.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.C/C++.General
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.General
- VS.ToolsOptionsPages.Text_Editor.CSS.General
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.General
- VS.ToolsOptionsPages.Text_Editor.F#.General
- VS.ToolsOptionsPages.Text_Editor.Fsharp.General
- VS.ToolsOptionsPages.Text_Editor.HQL.General
- VS.ToolsOptionsPages.Text_Editor.HTML.General
- VS.ToolsOptionsPages.Text_Editor.HTML_(Web_Forms).General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.General
- VS.ToolsOptionsPages.Text_Editor.JSON.General
- VS.ToolsOptionsPages.Text_Editor.LESS.General
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.General
- VS.ToolsOptionsPages.Text_Editor.SCSS.General
- VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.General
- VS.ToolsOptionsPages.Text_Editor.U-SQL.General
- VS.ToolsOptionsPages.Text_Editor.XAML.General
- VS.ToolsOptionsPages.Text_Editor.XML.General
helpviewer_keywords:
- Text Editor Options dialog box
- statement completion
- word wrap
- General dialog box
- line numbers
- virtual space
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9815bdec94ce32a3bfcc170dd95d834bc43ea58f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75566876"
---
# <a name="options-dialog-box-text-editor--all-languages"></a>Options, boîte de dialogue : éditeur de texte \> tous les langages

Cette boîte de dialogue vous permet de modifier le comportement par défaut de l’éditeur de code. Ces paramètres s’appliquent également à d’autres éditeurs basés sur l’éditeur de code, tels que le mode Source du concepteur HTML. Pour ouvrir cette boîte de dialogue, sélectionnez **Options** dans le menu **Outils**. Dans le dossier **Éditeur de texte**, développez le sous-dossier **Tous les langages**, puis choisissez **Général**.

> [!CAUTION]
> Cette page définit les options par défaut pour tous les langages de développement. N’oubliez pas que la réinitialisation d’une option dans cette boîte de dialogue entraîne la réinitialisation des options générales dans tous les langages quels que soient les choix effectués. Pour modifier les options de l’éditeur de texte pour un seul langage, développez le sous-dossier de ce langage et sélectionnez ses pages d’options.

Une coche grisée s’affiche quand une option a été sélectionnée dans les pages d’options générales pour certains langages de programmation mais pas pour d’autres.

## <a name="statement-completion"></a>Compléter automatiquement les instructions

**Répertorier automatiquement les membres**

Lorsque cette option est sélectionnée, les listes contextuelles des membres disponibles, les propriétés, les valeurs ou les méthodes sont affichées par IntelliSense lorsque vous tapez dans l’éditeur. Sélectionnez un élément dans la liste contextuelle pour l'insérer dans votre code. La sélection de cette option active l’option **Masquer les membres avancés**.

**Masquer les membres avancés**

Lorsque cette option est activée, les listes de saisie semi-automatique d’instructions contextuelles se limitent à l’affichage des éléments les plus couramment utilisés. D'autres éléments sont filtrés dans la liste.

**Informations sur les paramètres**

Lorsque cette option est sélectionnée, la syntaxe complète de la procédure ou déclaration actuelle s’affiche sous le point d’insertion dans l’éditeur, avec tous ses paramètres disponibles. Le paramètre suivant qui peut être affecté est affiché en gras.

## <a name="settings"></a>Paramètres

**Activer l'espace virtuel**

Lorsque cette option est sélectionnée et que l’option **Retour automatique à la ligne** est désactivée, vous pouvez cliquer hors de la limite d’une ligne de l’éditeur de code et saisir du texte. Cette fonctionnalité peut être utilisée pour placer des commentaires à un point précis en regard de votre code.

**Retour automatique à la ligne**

Lorsque cette option est sélectionnée, toute partie d’une ligne qui dépasse horizontalement de la zone affichable de l’éditeur est automatiquement affichée à la ligne suivante. La sélection de cette option active l’option **Afficher des glyphes visuels pour le retour automatique à la ligne**.

> [!NOTE]
> La fonctionnalité **Espace virtuel** est désactivée quand l’option **Retour automatique à la ligne** est activée.

**Afficher des glyphes visuels pour le retour automatique à la ligne**

Lorsque cette option est sélectionnée, un indicateur fléché de retour s’affiche à l’endroit où une ligne longue est automatiquement renvoyée à une deuxième ligne.

![Capture d'écran LineBreakSymbol](../../ide/reference/media/linebreak.gif)

Désactivez cette option si vous préférez ne pas afficher ces indicateurs.

> [!NOTE]
> Ces flèches de rappel ne sont pas ajoutées à votre code et ne sont pas imprimées. Ils servent de référence uniquement.

**Numéros de ligne**

Lorsque cette option est sélectionnée, un numéro de ligne apparaît en regard de chaque ligne de code.

> [!NOTE]
> Ces numéros de lignes ne sont pas ajoutés à votre code et ne sont pas imprimés. Ils servent de référence uniquement.

**Activer la navigation dans les URL par simple clic**

Lorsque cette option est sélectionnée, le curseur de souris prend la forme d’une main avec un doigt pointé lorsqu’il passe sur une URL dans l’éditeur. Vous pouvez cliquer sur l’URL pour afficher la page indiquée dans votre navigateur web.

**Barre de navigation**

Lorsque cette option est sélectionnée, la **barre de navigation** est affichée en haut de l’éditeur de code. Ses listes déroulantes **Objets** et **Membres** vous permettent de choisir un objet particulier dans votre code, de sélectionner parmi ses membres et d’accéder à la déclaration du membre sélectionné dans l’éditeur de code.

**Appliquer les commandes Couper ou Copier aux lignes vides en l'absence de sélection**

Cette option définit le comportement de l’éditeur lorsque vous placez le point d’insertion sur une ligne vide, ne sélectionnez rien, puis effectuez une action Copier ou Couper.

- Lorsque cette option est sélectionnée, la ligne vide est copiée ou coupée. Si vous effectuez ensuite une action Coller, une nouvelle ligne vide est insérée.

- Lorsque cette option est désactivée, la commande Couper supprime les lignes vides. Toutefois, les données figurant dans le Presse-papiers sont conservées. Par conséquent, si vous utilisez ensuite la commande Coller, le contenu le plus récemment copié dans le Presse-papiers est collé. Si aucune sélection n'a été copiée précédemment, aucune sélection n'est collée.

Ce paramètre n’a aucun effet sur les actions Copier ni Couper lorsqu’une ligne n’est pas vide. Si aucun élément n'est sélectionné, la totalité de la ligne est copiée ou coupée. Si vous effectuez ensuite une action Coller, le texte de la ligne toute entière et son caractère de ligne de fin sont collés.

> [!TIP]
> Pour afficher les indicateurs d’espaces, de tabulations et de fins de ligne et distinguer ainsi les lignes en retrait de celles qui sont complètement vides, sélectionnez **Avancé** dans le menu **Edition**, puis choisissez **Afficher les espaces blancs**.

## <a name="see-also"></a>Voir aussi

- [Options, Éditeur de texte, Tous les langages, Tabulations](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Général, environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)
- [Utilisation d’IntelliSense](../../ide/using-intellisense.md)
