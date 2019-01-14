---
title: Navigateur web, Environnement, boîte de dialogue Options
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.Environment.Web Browser
- VS.ToolsOptionsPages.Environment.WebBrowser
- VS.ToolsOptionsPages.Environment.Web_Browser
helpviewer_keywords:
- browsers, customizing
- searching, search page for Web browser
- Visual Studio Start page, default URL
- Web browsers, customizing
- searches, default Web browser search page
- URLs, specifying VS home page
- home page
- Options dialog box, Web settings
- Internet Explorer, setting options
ms.assetid: 586db4eb-032d-4cb5-93a6-a7c14de1ae49
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9bdfc727e3214292aade933abde6d6671c4b02fe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53955157"
---
# <a name="web-browser-environment-options-dialog-box"></a>Navigateur web, Environnement, boîte de dialogue Options

Définit les options à la fois pour le navigateur web interne et pour Internet Explorer. Pour accéder à cette boîte de dialogue, cliquez sur **Options** dans le menu **Outils**, développez le dossier **Environnement**, puis sélectionnez **Navigateur web**.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Réinitialiser les paramètres](../environment-settings.md#reset-settings).

> [!IMPORTANT]
> L’ouverture de certains fichiers ou composants à partir du web peut entraîner l’exécution de code sur votre ordinateur.

## <a name="home-page"></a>Page d'accueil

Définit la page affichée quand vous ouvrez le navigateur web de l’IDE.

## <a name="search-page"></a>Page de recherche

Vous permet de désigner une page de recherche pour le navigateur web interne. Cet emplacement peut différer de la page de recherche utilisée par des instances d’Internet Explorer lancées en dehors de l’environnement de développement intégré (IDE).

## <a name="view-source-in"></a>Afficher la source dans

Définit l’éditeur utilisé pour ouvrir une page web quand vous choisissez **Afficher la source** dans la page à partir du navigateur web interne.

-   **Éditeur de code source** Sélectionnez cette option pour afficher le code source dans [l’éditeur](../../ide/writing-code-in-the-code-and-text-editor.md).

-   **Éditeur HTML** Sélectionnez cette option pour afficher le code source dans le [concepteur HTML](https://msdn.microsoft.com/Library/640043cc-3657-4677-a091-bc315e636477). Utilisez cette sélection pour modifier la page web dans l’une des deux vues : en mode Création ou dans la vue Source standard basée sur du texte.

-   **Éditeur externe** Sélectionnez cette option pour afficher le code source dans un autre éditeur. Spécifiez le chemin de l’éditeur de votre choix, par exemple Notepad.exe.

## <a name="internet-explorer-options"></a>Options Internet Explorer

Cliquez sur ce bouton pour modifier les options relatives à Internet Explorer dans la boîte de dialogue **Propriétés Internet**. Les modifications apportées dans cette boîte de dialogue affectent à la fois le navigateur web interne et les instances d’Internet Explorer lancées en dehors de l’IDE de Visual Studio (par exemple, à partir du menu Démarrer).

> [!NOTE]
> Utilisez la boîte de dialogue **Naviguer avec** pour remplacer le navigateur web interne de Visual Studio par un navigateur de votre choix. Vous pouvez accéder à la boîte de dialogue Naviguer avec pour, par exemple, un fichier HTML dans votre projet en cliquant dessus avec le bouton droit ou en utilisant son menu contextuel.

## <a name="see-also"></a>Voir aussi

- [Environnement, boîte de dialogue Options](../../ide/reference/environment-options-dialog-box.md)
- [Général, Environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)
- [Concepteur HTML](https://msdn.microsoft.com/Library/640043cc-3657-4677-a091-bc315e636477)