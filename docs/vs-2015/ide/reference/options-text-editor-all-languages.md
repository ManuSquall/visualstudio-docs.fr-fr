---
title: Options, Éditeur de texte, Tous les langages | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.ResJSON.General
- vs.toolsoptionspages.text_editor.all_languages.scrollbars
helpviewer_keywords:
- Text Editor Options dialog box
- statement completion
- word wrap
- General dialog box
- line numbers
- virtual space
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ebe2da1dec9917a792f3e4e02516a79cff605c80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662400"
---
# <a name="options-text-editor-all-languages"></a>Options, Éditeur de texte, Tous les langages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cette boîte de dialogue vous permet de modifier le comportement par défaut de l’éditeur de code. Ces paramètres s’appliquent également à d’autres éditeurs basés sur l’éditeur de code, tels que le mode Source du concepteur HTML. Pour ouvrir cette boîte de dialogue, sélectionnez **Options** dans le menu **Outils**. Dans le dossier **Éditeur de texte**, développez le sous-dossier **Tous les langages**, puis choisissez **Général**.

> [!CAUTION]
> Cette page définit les options par défaut pour tous les langages de développement. N’oubliez pas que la réinitialisation d’une option dans cette boîte de dialogue entraîne la réinitialisation des options générales dans tous les langages quels que soient les choix effectués. Pour modifier les options de l’éditeur de texte pour un seul langage, développez le sous-dossier de ce langage et sélectionnez ses pages d’options.

 Une coche grisée s’affiche quand une option a été sélectionnée dans les pages d’options générales pour certains langages de programmation mais pas pour d’autres.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l'Aide selon les paramètres actifs ou le mode d'édition. Pour modifier vos paramètres, choisissez **Paramètres d'importation et d'exportation** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="statement-completion"></a>Compléter automatiquement les instructions
 Répertorier automatiquement les membres quand ils sont sélectionnés, les listes contextuelles des membres, propriétés, valeurs ou méthodes disponibles sont affichées par IntelliSense lorsque vous tapez dans l’éditeur. Sélectionnez un élément dans la liste contextuelle pour l'insérer dans votre code. La sélection de cette option active l’option **Masquer les membres avancés**.

 Masquer les membres avancés : lorsque cette option est sélectionnée, les listes de saisie semi-automatique des instructions contextuelles sont réduites en affichant uniquement les éléments les plus couramment utilisés. D'autres éléments sont filtrés dans la liste.

 Informations sur les paramètres quand elles sont sélectionnées, la syntaxe complète de la déclaration ou de la procédure actuelle s’affiche sous le point d’insertion dans l’éditeur, avec tous ses paramètres disponibles. Le paramètre suivant qui peut être affecté est affiché en gras.

## <a name="settings"></a>Paramètres
 Activer l’espace virtuel quand cette option est sélectionnée et que le **retour** automatique à la ligne est désactivé, vous pouvez cliquer n’importe où au-delà de la fin d’une ligne dans l’éditeur de code et taper. Cette fonctionnalité peut être utilisée pour placer des commentaires à un point précis en regard de votre code.

 Retour automatique à la ligne quand vous sélectionnez cette option, toute partie d’une ligne qui s’étend horizontalement au-delà de la zone de l’éditeur affichable est automatiquement affichée sur la ligne suivante. La sélection de cette option active l’option **Afficher des glyphes visuels pour le retour automatique à la ligne**.

> [!NOTE]
> La fonctionnalité **Espace virtuel** est désactivée quand l’option **Retour automatique à la ligne** est activée.

 Afficher les glyphes visuels pour le retour automatique à la ligne lorsque cette option est sélectionnée, un indicateur de flèche de retour s’affiche à l’endroit où une ligne longue est automatiquement renvoyée sur une deuxième ligne.

 ![Capture d’écran LineBreakSymbol](../../ide/reference/media/linebreak.gif "linebreak")

 Désactivez cette option si vous préférez ne pas afficher ces indicateurs.

> [!NOTE]
> Ces flèches de rappel ne sont pas ajoutées à votre code et ne sont pas imprimées. Ils servent de référence uniquement.

 Appliquer les commandes Couper ou copier aux lignes vides en l’absence de sélection cette option définit le comportement de l’éditeur lorsque vous placez le point d’insertion sur une ligne vide, ne sélectionnez rien, puis copiez ou coupez.

- Lorsque cette option est sélectionnée, la ligne vide est copiée ou coupée. Si vous effectuez ensuite une action Coller, une nouvelle ligne vide est insérée.

- Lorsque cette option est désactivée, la commande Couper supprime les lignes vides. Toutefois, les données figurant dans le Presse-papiers sont conservées. Par conséquent, si vous utilisez ensuite la commande Coller, le contenu le plus récemment copié dans le Presse-papiers est collé. Si aucune sélection n'a été copiée précédemment, aucune sélection n'est collée.

  Ce paramètre n’a aucun effet sur les actions Copier ni Couper lorsqu’une ligne n’est pas vide. Si aucun élément n'est sélectionné, la totalité de la ligne est copiée ou coupée. Si vous effectuez ensuite une action Coller, le texte de la ligne toute entière et son caractère de ligne de fin sont collés.

> [!TIP]
> Pour afficher les indicateurs d’espaces, de tabulations et de fins de ligne et distinguer ainsi les lignes en retrait de celles qui sont complètement vides, sélectionnez **Avancé** dans le menu **Edition**, puis choisissez **Afficher les espaces blancs**.

## <a name="display"></a>Afficher
 Numéros de ligne lorsque cette option est sélectionnée, un numéro de ligne apparaît en regard de chaque ligne de code.

> [!NOTE]
> Ces numéros de lignes ne sont pas ajoutés à votre code et ne sont pas imprimés. Ils servent de référence uniquement.

 Activer la navigation dans les URL par simple clic quand elle est sélectionnée, le curseur de la souris prend la forme d’une main de pointage lorsqu’il passe sur une URL dans l’éditeur. Vous pouvez alors cliquer sur l'URL pour afficher la page correspondante dans votre navigateur Web.

 Barre de navigation quand elle est sélectionnée, affiche la **barre de navigation** en haut de l’éditeur de code. Ses listes déroulantes **Objets** et **Membres** vous permettent de choisir un objet particulier dans votre code, de sélectionner parmi ses membres et d’accéder à la déclaration du membre sélectionné dans l’éditeur de code.

## <a name="see-also"></a>Voir aussi
 [Options, éditeur de texte, tous les langages, onglets](../../ide/reference/options-text-editor-all-languages-tabs.md) [général, environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md) [avec IntelliSense](../../ide/using-intellisense.md)
