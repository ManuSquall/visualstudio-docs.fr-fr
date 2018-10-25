---
title: Visual C++ IntelliSense | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9d7c6414-4e6c-4889-a74c-a6033795eccc
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ced999c20678cc64dc5f96e86070b5f39d5ca2c7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881675"
---
# <a name="visual-c-intellisense"></a>Visual C++ Intellisense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans Visual Studio 2015, IntelliSense peut être utilisé avec des fichiers de code individuels, mais aussi avec des fichiers de projets. Dans les projets interplateforme, certaines fonctionnalités IntelliSense sont disponibles avec les fichiers .cpp et .c du projet de code partagé, y compris dans un contexte Android ou iOS.  
  
## <a name="intellisense-features-in-c"></a>Fonctionnalités IntelliSense en C++  
 IntelliSense est le nom d’un ensemble de fonctionnalités conçues pour faciliter le codage. Quasiment toutes les fonctionnalités IntelliSense peuvent être activées ou désactivées via la page de propriétés **Éditeur de texte, C/C++, Avancé**. Chaque développeur peut ainsi choisir les fonctionnalités qui lui semblent utiles.  
  
 ![Outils, options, éditeur de texte, C/C++, avancé](../ide/media/sintellisensecpptoolsoptions.PNG "sIntelliSenseCppToolsOptions")  
  
 Vous pouvez utiliser les éléments de menu et les raccourcis clavier indiqués dans l'image suivante pour accéder à IntelliSense.  
  
 ![Menu IntelliSense Visual C++](../ide/media/vs2015-cpp-intellisense-menu.png "vs2015_cpp_intellisense_menu")  
  
### <a name="statement-completion-and-member-list"></a>Saisie semi-automatique des instructions et liste des membres  
 Quand vous commencez à taper un mot clé, un type, une fonction, un nom de variable ou tout autre élément de code reconnu par le compilateur, l'éditeur vous propose de compléter automatiquement la chaîne.  
  
 Pour obtenir la liste des icônes et leurs significations, consultez [Affichage de classes et Explorateur d’objets, icônes](../ide/class-view-and-object-browser-icons.md).  
  
 ![Fenêtre Compléter le mot Visual C++](../ide/media/vs2015-cpp-complete-word.png "vs2015_cpp_complete_word")  
  
 Au premier appel de la liste des membres, cette liste affiche uniquement les membres qui sont accessibles pour le contexte actuel. Si vous appelez ensuite cette liste avec **Ctrl+J**, elle affiche tous les membres indépendamment de leur accessibilité. Si vous l'appelez une troisième fois, la liste qui s'affiche présente encore plus d'éléments de code. Vous pouvez désactiver la saisie semi-automatique des instructions dans la page **Options générales de C/C++**.  
  
 ![Liste de membres Visual C++](../ide/media/vs2015-cpp-list-members.png "vs2015_cpp_list_members")  
  
### <a name="parameter-help"></a>Aide sur les paramètres  
 Quand vous tapez une accolade ouvrante dans un appel de fonction, ou un crochet pointu dans une déclaration de variable de modèle de classe, l'éditeur ouvre une petite fenêtre qui affiche les types de paramètre pour chaque surcharge de la fonction ou du constructeur. Le paramètre « actuel », basé sur l'emplacement du curseur, est indiqué en gras. Vous pouvez désactiver la saisie semi-automatique des instructions dans la page **Options générales de C/C++**.  
  
 ![Aide sur les paramètres Visual C++](../ide/media/vs-2015-cpp-param-help.png "vs_2015_cpp_param_help")  
  
### <a name="quick-info"></a>Info express  
 Quand vous placez le curseur sur une variable, une petite fenêtre inline s'affiche, présentant les informations de type et l'en-tête où le type est défini. Placez le curseur sur un appel de fonction pour afficher la signature de la fonction. Vous pouvez désactiver la fonctionnalité Info express dans la page **Éditeur de texte, C/C++, Avancé**.  
  
 ![Info Express Visual C++](../ide/media/vs2015-cpp-quickinfo.png "vs2015_cpp_quickInfo")  
  
## <a name="error-squiggles"></a>Tildes d'erreur  
 Les tildes affichés sous un élément de code (variable, mot clé, accolade, nom de type, etc.) signalent une erreur réelle ou potentielle dans le code. Quand vous écrivez une déclaration anticipée, un tilde vert s'affiche pour vous rappeler que vous devez encore écrire l'implémentation. Un tilde violet s'affiche dans un projet partagé pour signaler une erreur dans du code qui n'est pas encore actif. C'est le cas, par exemple, quand vous travaillez dans le contexte Windows et que vous entrez du code qui serait erroné dans un contexte Android. Un tilde rouge indique une erreur ou un avertissement de compilateur, dans le code actif, que vous devez traiter.  
  
 ![Tildes d’erreur Visual C++](../ide/media/vs2015-cpp-error-quiggles.png "vs2015_cpp_error_quiggles")  
  
## <a name="code-colorization-and-fonts"></a>Colorisation et polices du code  
 Les couleurs et les polices par défaut peuvent être modifiées via la page de propriétés **Environnement, Polices et couleurs**. Vous pouvez modifier les polices pour de nombreuses fenêtres d'interface utilisateur ici, et pas seulement l'éditeur. Les paramètres spécifiques du langage C++ commencent par « C++ » ; les autres paramètres s'appliquent à tous les langages.  
  
## <a name="cross-platform-intellisense"></a>IntelliSense interplateforme  
 Dans un projet de code partagé, certaines fonctionnalités IntelliSense, telles que les tildes, restent toujours disponibles, y compris dans un contexte Android. Si vous écrivez du code qui générerait une erreur dans un projet inactif, IntelliSense affiche des tildes d'une couleur différente de celle des tildes d'erreur indiqués pour le contexte actuel.  
  
 Voici une application OpenGLES configurée pour la génération Android et iOS. L'illustration montre le code partagé en cours de modification. Dans la première image, Android est le projet actif :  
  
 ![Le projet Android est le projet actif](../ide/media/intellisensecppcrossplatform.png "IntelliSenseCppCrossPlatform")  
  
 Notez les points suivants :  
  
- Le #else branche sur la ligne 8 est grisée pour indiquer une région inactive, car `__ANDROID__` est défini pour le projet Android.  
  
- La variable de salutations à la ligne 11 est initialisée avec l'identificateur HELLO, qui comporte un tilde violet. En effet, aucun identificateur HELLO n'est défini dans le projet iOS inactif. Dans un projet Android, la ligne 11 est compilée, alors que ce n'est pas le cas dans un projet iOS. Comme il s'agit de code partagé, vous devez changer cela même si la compilation aboutit dans la configuration active.  
  
- La ligne 12 a un tilde rouge sous l'identificateur BYE. Cet identificateur n'est pas défini dans le projet actif sélectionné.  
  
  À présent, remplacez le projet actif en iOS.StaticLibrary, et notez la façon dont les tildes changent.  
  
  ![iOS est sélectionné comme projet actif](../ide/media/intellisensecppcrossplatform2.png "IntelliSenseCppCrossPlatform2")  
  
  Notez les points suivants :  
  
- La branche #ifdef sur la ligne 6 est grisée pour indiquer une région inactive, car *_ANDROID\\*  \_ n’est pas défini pour le projet iOS.  
  
- La variable de salutations à la ligne 11 est initialisée avec l'identificateur HELLO, qui comporte à présent un tilde rouge. En effet, aucun identificateur HELLO n'est défini dans le projet iOS actif.  
  
- La ligne 12 a un tilde violet sous l'identificateur BYE. Cet identificateur n'est pas défini dans le projet inactif Android.NativeActivity.  
  
## <a name="single-file-intellisense"></a>IntelliSense avec un fichier unique  
 IntelliSense est également disponible quand vous ouvrez un seul fichier en dehors de tout projet. Vous pouvez activer ou désactiver les fonctionnalités de votre choix, par exemple IntelliSense, dans la page de propriétés **Éditeur de texte, C/C++, Avancé**. Si vous souhaitez configurer IntelliSense pour des fichiers uniques qui ne font pas partie d’un projet, recherchez **IntelliSense et accès aux fichiers hors projet** dans la section **Avancé**. Consultez [Visite guidée de Visual C++](http://msdn.microsoft.com/en-us/499cb66f-7df1-45d6-8b6b-33d94fd1f17c).  
  
 ![IntelliSense avec un fichier unique](../ide/media/vs2015-cpp-single-file-intellisense.png "vs2015_cpp_single_file_intellisense")  
  
 Par défaut, IntelliSense pour fichier unique utilise uniquement les répertoires Include standard pour rechercher les fichiers d'en-tête. Pour ajouter d’autres répertoires, ouvrez le menu contextuel du nœud Solution, puis ajoutez votre répertoire à la liste **Déboguer le code source**, comme le montre l’illustration suivante :  
  
 ![Ajout d’un chemin à un fichier d’en-tête](../ide/media/intellisensedebugyourcode.jpg "IntelliSenseDebugYourCode")  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de la fonctionnalité IntelliSense](../ide/using-intellisense.md)



