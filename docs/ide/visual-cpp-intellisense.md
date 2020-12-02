---
title: IntelliSense pour C++
description: Découvrez certaines fonctionnalités IntelliSense que vous pouvez utiliser lors du codage de votre projet C++.
ms.custom: SEO-VS-2020
ms.date: 10/08/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 49d555b2e509237e34375e1b85a35c57a6db4f3b
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96478885"
---
# <a name="visual-c-intellisense-features"></a>Fonctionnalités IntelliSense pour Visual C++

IntelliSense est le nom d’un ensemble de fonctionnalités conçues pour faciliter le codage. IntelliSense pour C++ peut être utilisé avec des fichiers autonomes, mais aussi avec des fichiers qui font partie d’un projet C++. Dans les projets multiplateformes, certaines fonctionnalités IntelliSense sont disponibles dans les fichiers *. cpp* et *. c* du projet de code partagé, même si vous êtes dans un contexte Android ou iOS.

Cet article présente une vue d’ensemble des fonctionnalités IntelliSense C++. Pour plus d’informations sur la configuration des projets pour IntelliSense et la résolution des problèmes, voir [Configurer un projet C++ pour IntelliSense](visual-cpp-intellisense-configuration.md).

## <a name="intellisense-features-in-c"></a>Fonctionnalités IntelliSense en C++

IntelliSense est le nom d’un ensemble de fonctionnalités conçues pour faciliter le codage. Étant donné que chaque utilisateur a sa propre opinion sur ce qui est pratique, pratiquement toutes les fonctionnalités IntelliSense peuvent être activées ou désactivées dans la boîte de dialogue **Options** sous **Éditeur de texte** > **C/C++** > **Avancé**. La boîte de dialogue **Options** est accessible dans le menu **Outils** dans la barre de menus.

![Boîte de dialogue Options d’outil](../ide/media/sintellisensecpptoolsoptions.PNG)

Vous pouvez utiliser les éléments de menu et les raccourcis clavier indiqués dans l'image suivante pour accéder à IntelliSense.

![Menu IntelliSense](../ide/media/vs2015_cpp_intellisense_menu.png)

## <a name="statement-completion-and-member-list"></a>Saisie semi-automatique des instructions et liste des membres

Quand vous commencez à taper un mot clé, un type, une fonction, un nom de variable ou tout autre élément de code reconnu par le compilateur, l'éditeur vous propose de compléter automatiquement la chaîne.

Pour obtenir la liste des icônes et leurs significations, consultez [affichage de classes et icônes](../ide/class-view-and-object-browser-icons.md)de l’Explorateur d’objets.

![Fenêtre Compléter le mot de Visual C&#43;&#43;](../ide/media/vs2015_cpp_complete_word.png)

Au premier appel de la liste des membres, seuls les membres accessibles dans le contexte actuel sont affichés. Si vous appuyez sur **CTRL** + **J** après cela, il affiche tous les membres indépendamment de l’accessibilité. Si vous l'appelez une troisième fois, la liste qui s'affiche présente encore plus d'éléments de code. Vous pouvez désactiver la liste des membres dans la boîte de dialogue **Options** sous **Éditeur de texte** > **C/C++** > **Général** > **Répertorier automatiquement les membres**.

![Liste de membres Visual C&#43;&#43;](../ide/media/vs2015_cpp_list_members.png)

## <a name="parameter-help"></a>Aide sur les paramètres

Quand vous tapez une accolade ouvrante dans un appel de fonction, ou un crochet pointu dans une déclaration de variable de modèle de classe, l'éditeur ouvre une petite fenêtre qui affiche les types de paramètre pour chaque surcharge de la fonction ou du constructeur. Le paramètre « actuel »&mdash;basé sur l'emplacement du curseur&mdash;est indiqué en gras. Vous pouvez désactiver les informations de paramètre dans la boîte de dialogue **Options** sous **Éditeur de texte** > **C/C++** > **Général** > **Informations de paramètre**.

![Aide sur les paramètres Visual C&#43;&#43;](../ide/media/vs_2015_cpp_param_help.png)

## <a name="quick-info"></a>Infos express

Quand vous placez le curseur sur une variable, une petite fenêtre inline s'affiche, présentant les informations de type et l'en-tête où le type est défini. Placez le curseur sur un appel de fonction pour afficher la signature de la fonction. Vous pouvez désactiver la fonctionnalité Info express dans la boîte de dialogue **Options** sous **Éditeur de texte** > **C/C++** > **Avancé** > **Info express auto**.

![Info Express Visual C&#43;&#43;](../ide/media/vs2015_cpp_quickinfo.png)

## <a name="error-squiggles"></a>Tildes d'erreur

Les tildes affichés sous un élément de code (variable, mot clé, accolade, nom de type, etc.) signalent une erreur réelle ou potentielle dans le code. Quand vous écrivez une déclaration anticipée, un tilde vert s'affiche pour vous rappeler que vous devez encore écrire l'implémentation. Un tilde violet s'affiche dans un projet partagé pour signaler une erreur dans du code qui n'est pas encore actif. C'est le cas, par exemple, quand vous travaillez dans le contexte Windows et que vous entrez du code qui serait erroné dans un contexte Android. Un tilde rouge indique une erreur ou un avertissement de compilateur, dans le code actif, que vous devez traiter.

![Tildes d’erreur Visual C&#43;&#43;](../ide/media/vs2015_cpp_error_quiggles.png)

### <a name="code-colorization-and-fonts"></a>Colorisation et polices du code

Les couleurs par défaut et les polices peuvent être modifiés dans la boîte de dialogue **Options** sous **Environnement** > **Polices et couleurs**. Vous pouvez modifier les polices pour de nombreuses fenêtres d'interface utilisateur ici, et pas seulement l'éditeur. Les paramètres spécifiques du langage C++ commencent par « C++ » ; les autres paramètres s'appliquent à tous les langages.

## <a name="cross-platform-intellisense"></a>IntelliSense multiplateforme

Dans un projet de code partagé, certaines fonctionnalités IntelliSense, telles que les tildes, restent toujours disponibles, y compris dans un contexte Android. Si vous écrivez du code qui générerait une erreur dans un projet inactif, IntelliSense affiche des tildes d'une couleur différente de celle des tildes d'erreur indiqués pour le contexte actuel.

Considérez une application OpenGLES configurée pour la génération Android et iOS. L'illustration montre le code partagé en cours de modification. Dans cette image, le projet actif est **iOS.StaticLibrary** :

![iOS est sélectionné comme projet actif.](../ide/media/intellisensecppcrossplatform2.png)

Notez les points suivants :

- La branche `#ifdef` sur la ligne 6 est en grisé pour indiquer une région inactive, car `__ANDROID__` n’est pas défini pour un projet iOS.

- La variable greeting à la ligne 11 est initialisée avec l’identificateur `HELLO`, qui comporte à présent un tilde rouge. En effet, aucun identificateur `HELLO` n’est défini dans le projet iOS actuellement actif.

- La ligne 12 a un tilde violet sous l’identificateur `BYE`, car celui-ci n’est pas défini dans le projet **Android.NativeActivity** (actuellement) inactif. Bien que cette ligne soit compilée quand iOS est le projet actif, elle n’est pas compilée quand Android est le projet actif. Comme il s’agit de code partagé, vous devez corriger le code même s’il est compilé correctement dans la configuration active.

Si vous changez le projet actif pour Android, les tildes changent :

- La branche `#else` sur la ligne 8 est en grisé pour indiquer une région inactive, car `__ANDROID__` est défini pour un projet Android.

- La variable greeting à la ligne 11 est initialisée avec l’identificateur `HELLO`, qui comporte un tilde violet. En effet, aucun identificateur `HELLO` n’est défini dans le projet iOS actuellement inactif.

- La ligne 12 a un tilde rouge sous l’identificateur `BYE`, car celui-ci n’est pas défini dans le projet actif.

## <a name="intellisense-for-stand-alone-files"></a>IntelliSense pour les fichiers autonomes

IntelliSense est également disponible quand vous ouvrez un seul fichier en dehors de tout projet. Vous pouvez activer ou désactiver les fonctionnalités IntelliSense dans la boîte de dialogue **Options** sous **Éditeur de texte** > **C/C++** > **Avancé**. Si vous souhaitez configurer IntelliSense pour des fichiers individuels qui ne font pas partie d’un projet, recherchez la section **IntelliSense et accès aux fichiers hors projet**.

![IntelliSense avec un fichier unique Visual C&#43;&#43;](../ide/media/vs2015_cpp_single_file_intellisense.png)

Par défaut, IntelliSense pour fichier unique utilise uniquement les répertoires Include standard pour rechercher les fichiers d'en-tête. Pour ajouter d’autres répertoires, ouvrez le menu contextuel du nœud **Solution**, puis ajoutez votre répertoire à la liste **Déboguer le code source**, comme le montre l’illustration suivante :

![Ajout d'un chemin d'accès à un fichier d'en-tête.](../ide/media/intellisensedebugyourcode.jpg)

## <a name="enable-or-disable-features"></a>Activer ou désactiver des fonctionnalités

Étant donné que chaque utilisateur a sa propre opinion sur ce qui est pratique, pratiquement toutes les fonctionnalités IntelliSense peuvent être activées ou désactivées dans la boîte de dialogue **Options** sous **Éditeur de texte** > **C/C++** > **Avancé**. La boîte de dialogue **Options** est accessible dans le menu **Outils** dans la barre de menus.

![Boîte de dialogue Options d’outil](../ide/media/sintellisensecpptoolsoptions.PNG)

## <a name="see-also"></a>Voir aussi

- [Utilisation d’IntelliSense](../ide/using-intellisense.md)
- [Configurer un projet C++ pour IntelliSense](visual-cpp-intellisense-configuration.md)
