---
title: Options, Éditeur de texte, C/C++, Avancé
description: Découvrez comment utiliser la page avancé de la section C/C++ pour modifier le comportement lié à IntelliSense et à la base de données de navigation.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C\C++.Advanced
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Advanced
- VS.ToolsOptionsPages.Text_Editor.C/C++.Advanced
helpviewer_keywords:
- Text Editor Options dialog box, advanced
ms.assetid: 67c82ae5-fddd-49df-baec-8e7498b156f3
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: fe69471d231599c6e3eece0b56ff70fca5b6afab
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040340"
---
# <a name="options-text-editor-cc-advanced"></a>Options, Éditeur de texte, C/C++, Avancé

En modifiant ces options, vous pouvez changer le comportement lié à IntelliSense et la base de données de navigation quand vous programmez en C ou C++.

Pour accéder à cette page, dans le volet gauche de la boîte de dialogue **Options**, développez **Éditeur de texte**, **C/C++**, puis choisissez **Avancé**.

> [!NOTE]
> Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Consultez [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="browsingnavigation"></a>Navigation de fichiers/répertoires

Vous ne devez jamais utiliser ces options, sauf dans les rares cas où une solution est tellement volumineuse que l’activité de base de données consomme une quantité inacceptable de ressources système.

**Désactiver la base de données**

Toutes les utilisations de la base de données de navigation du code (SDF), toutes les autres options de navigation de fichiers/répertoires et toutes les fonctionnalités IntelliSense, sauf la saisie semi-automatique des #include, sont désactivées.

**Désactiver les mises à jour de la base de données**

La base de données est ouverte en lecture seule et aucune mise à jour n’est effectuée pendant la modification des fichiers. La plupart des fonctionnalités continuent de fonctionner. Toutefois, à mesure que des modifications sont effectuées, les données deviennent obsolètes et vous obtenez des résultats incorrects.

**Désactiver les mises à jour automatiques de la base de données**

La base de données de navigation du code n’est pas automatiquement mise à jour quand les fichiers sources sont modifiés. Toutefois, si vous ouvrez l’**Explorateur de solutions**, puis le menu contextuel du projet et que vous choisissez **Relancer l’analyse de la solution**, tous les fichiers obsolètes sont vérifiés et la base de données est mise à jour.

**Désactiver les fichiers implicites**

La base de données de navigation du code ne collecte pas les données pour les fichiers qui ne sont pas spécifiés dans un projet. Un projet contient des fichiers sources et des fichiers d’en-tête qui sont explicitement spécifiés. Les fichiers implicites sont inclus par les fichiers explicites (par exemple, afxwin.h, windows.h et atlbase.h). Normalement, le système recherche ces fichiers et les indexe également pour diverses fonctionnalités de navigation (notamment Accéder à). Si vous choisissez cette option, ces fichiers ne sont pas indexés et certaines fonctionnalités ne sont pas disponibles pour eux. Si vous choisissez cette option, les options « Désactiver le nettoyage implicite » et « Désactiver les dépendances externes » sont également implicitement choisies.

**Désactiver le nettoyage implicite**

La base de données de navigation du code ne nettoie pas les fichiers implicites qui ne sont plus référencés. Cette option empêche les fichiers implicites d’être supprimés de la base de données quand ils ne sont plus utilisés. Par exemple, si vous ajoutez une directive `#include` qui référence mapi.h à l’un de vos fichiers sources, mapi.h est trouvé et indexé. Si vous supprimez ensuite la directive #include et que le fichier n’est pas référencé ailleurs, les informations le concernant sont supprimées, sauf si vous choisissez cette option. (Voir l’option **intervalle de nouvelle analyse** de la solution.) Cette option est ignorée quand vous effectuez une nouvelle analyse de la solution de manière explicite.

**Activer les dossiers de dépendances externes**

Le dossier Dépendances externes pour chaque projet n’est pas créé ou mis à jour. Dans l’**Explorateur de solutions**, chaque projet a un dossier Dépendances externes qui contient tous les fichiers implicites pour ce projet. Si vous choisissez cette option, ce dossier n’apparaît pas.

**Recréer la base de données**

Recréez entièrement la base de données de navigation du code lors du prochain chargement de la solution. Si vous choisissez cette option, le fichier de base de données SDF est supprimé lors du prochain chargement de la solution, ce qui entraîne la recréation de la base de données et de tous les fichiers indexés.

**Intervalle de nouvelle analyse de la solution**

Un travail « Relancer l’analyse de la solution maintenant » est planifié pour l’intervalle que vous spécifiez. Vous devez spécifier une valeur entre 0 et 5 000 minutes. La valeur par défaut est 60 minutes. Pendant la nouvelle analyse de la solution, les horodateurs de fichiers sont vérifiés pour déterminer si un fichier a été modifié en dehors de l’IDE. (Les modifications apportées à l’IDE sont suivies automatiquement et les fichiers sont mis à jour.) Les fichiers inclus implicitement sont vérifiés pour déterminer s’ils sont toujours référencés.

## <a name="diagnostic-logging"></a>Journalisation des diagnostics

Ces options sont fournies au cas où Microsoft vous demande de collecter des informations avancées pour diagnostiquer un problème. Les informations de journalisation ne sont pas utiles pour les utilisateurs, et nous vous recommandons de laisser cette option désactivée.

**Activer la journalisation**

Active la journalisation des diagnostics dans la fenêtre de sortie.

**Niveau de journalisation**

Définir le niveau de détail du journal, de 0 à 5.

**Filtre de journalisation**

Les filtres affichent les types d’événements à l’aide d’un masque de bits.

Définissez cette option à l’aide d’une somme des options suivantes :

- 0 - Aucun

- 1 - Général

- 2 - Inactif

- 4 - Élément de travail

- 8 - IntelliSense

- 16 - ACPerf

- 32 - ClassView

## <a name="fallback-location"></a>Emplacement de secours

L’emplacement de secours est l’endroit où les fichiers de support IntelliSense et SDF (par exemple, iPCH) sont placés quand l’emplacement principal (même répertoire que la solution) n’est pas utilisé. Cette situation peut se produire si l’utilisateur n’a pas l’autorisation d’écrire dans le répertoire de solution ou si le répertoire de solution se trouve sur un appareil lent. L’emplacement de secours par défaut est le répertoire temp de l’utilisateur.

**Toujours utiliser l’emplacement de secours**

Indique que la base de données de navigation du code et les fichiers IntelliSense doivent toujours être stockés dans un dossier que vous spécifiez comme « Emplacement de secours », et non avec le fichier .sln. L’IDE n’essaie jamais de placer les fichiers SDF ou iPCH à côté du répertoire de solution et utilise toujours l’emplacement de secours.

**Ne pas avertir si l’emplacement de secours est utilisé**

Vous n’êtes pas informé ni sollicité si un « emplacement de secours » est utilisé. Normalement, l’IDE vous indique s’il a dû utiliser l’emplacement de secours. Cette option désactive cet avertissement.

**Emplacement de secours**

Cette valeur est utilisée comme emplacement secondaire pour stocker la base de données de navigation du code ou les fichiers IntelliSense. Par défaut, votre répertoire temporaire est votre emplacement de secours. L’IDE crée un sous-répertoire sous le chemin spécifié (ou le répertoire temp) qui inclut le nom de la solution avec un hachage du chemin complet de la solution, ce qui évite les problèmes de noms de solution identiques.

## <a name="intellisense"></a>IntelliSense

**Info express automatique**

Active les info-bulles Info express quand vous déplacez le pointeur sur le texte.

**Désactiver IntelliSense**

Désactive toutes les fonctionnalités IntelliSense. L’IDE ne crée pas de processus VCPkgSrv.exe pour traiter les demandes IntelliSense et aucune fonctionnalité IntelliSense ne fonctionne (Info express, Liste des membres, Saisie semi-automatique, Aide sur les paramètres). La colorisation sémantique et la mise en surbrillance des références sont également désactivées. Cette option ne désactive pas les fonctionnalités de navigation qui reposent uniquement sur la base de données (notamment la barre de navigation, ClassView et la fenêtre des propriétés).

**Désactiver la mise à jour automatique**

La mise à jour d’IntelliSense est retardée dans l’attente d’une demande pour IntelliSense. Ce délai peut entraîner une durée d’exécution plus longue de la première opération IntelliSense sur un fichier, mais cette option peut être utile pour des ordinateurs très lents ou avec des ressources limitées. Si vous choisissez cette option, vous choisissez également de manière implicite les options « Désactiver le rapport d’erreurs » et « Désactiver les tildes ».

**Désactiver le rapport d’erreurs**

Désactive le signalement des erreurs IntelliSense par des tildes et la fenêtre Liste d’erreurs. Désactive également l’analyse en arrière-plan associée au rapport d’erreurs. Si vous choisissez cette option, vous choisissez également de manière implicite l’option « Désactiver les tildes ».

**Désactiver les tildes**

Désactive les tildes d’erreur IntelliSense. Les « tildes » rouges ne s’affichent pas dans la fenêtre de l’éditeur, mais l’erreur apparaît toujours dans la fenêtre Liste d’erreurs.

**Réglage auto de Unités de traduction mises en cache maximum**

Nombre maximal d’unités de traduction qui restent actives à tout moment pour les demandes IntelliSense. Vous devez spécifier une valeur entre 2 et 15. Ce nombre est directement lié au nombre maximal de processus VCPkgSrv.exe qui s’exécutent (pour une instance donnée de Visual Studio). La valeur par défaut est 2, mais si vous avez de la mémoire disponible, vous pouvez augmenter cette valeur et éventuellement obtenir des performances légèrement supérieures dans IntelliSense.

Pour plus d’informations sur les unités de traduction, consultez [Phases de traduction](/cpp/preprocessor/phases-of-translation).

**Désactiver la saisie semi-automatique des #include**

Désactive la saisie semi-automatique des instructions `#include`.

**Utiliser la barre oblique dans la saisie semi-automatique des #include**

Déclenche la saisie semi-automatique des instructions `#include` quand « / » est utilisé. Le délimiteur par défaut est une barre oblique inverse ’\'. Le compilateur peut accepter les deux, donc utilisez cette option pour spécifier le délimiteur que votre base de code utilise.

**Désactiver la liste de membres agressifs**

La liste des membres n’apparaît pas quand vous tapez le nom d’un type ou d’une variable. La liste s’affiche uniquement quand vous tapez l’un des caractères de validation, comme défini dans l’option **Caractères de validation des listes de membres**.

**Désactiver les mots clés des listes de membres**

Les mots clés de langage comme `void`, `class`, `switch` n’apparaissent pas dans les suggestions des listes de membres.

**Désactiver les extraits de code des listes de membres**

Les extraits de code n’apparaissent pas dans les suggestions des listes de membres.

**Mode filtre des listes de membres**

Définit le type d’algorithme de correspondance. **Approximatif** recherche la correspondance la plus probable, car il utilise un algorithme similaire à un vérificateur d’orthographe pour rechercher les correspondances similaires, mais non identiques. **Filtrage intelligent** recherche des sous-chaînes, même si elles ne sont pas au début d’un mot. **Préfixe** recherche uniquement les sous-chaînes identiques qui démarrent au début du mot.

**Désactiver la colorisation sémantique**

Désactive toute la colorisation de code, à l’exception des mots clés de langage, des chaînes et des commentaires.

**Caractères de validation des listes de membres**

Spécifie les caractères qui entraînent la validation de la suggestion de liste de membres actuellement mise en surbrillance. Vous pouvez ajouter ou supprimer des caractères de la liste.

**Validation intelligente de la liste des membres**

Ajoute une ligne quand vous appuyez sur la touche Entrée à la fin du mot complet tapé.

**Activer la liste des membres point par flèche**

Remplace « . » par « -> » le cas échéant pour la liste des membres.

## <a name="references"></a>Références

**Désactiver la résolution**

Pour des motifs de performances, « Rechercher toutes les références » affiche par défaut les résultats de recherche en texte brut au lieu d’utiliser IntelliSense pour vérifier chaque candidat. Vous pouvez décocher cette case pour obtenir des résultats plus précis sur toutes les opérations de recherche. Pour appliquer des filtres par recherche, ouvrez le menu contextuel de la liste des résultats, puis choisissez « Résoudre les résultats ».

**Masquer les éléments non confirmés**

Masquez les éléments non confirmés dans les résultats de « Rechercher toutes les références ». Si vous annulez l’option « Désactiver la résolution », vous pouvez utiliser cette option pour masquer les éléments non confirmés dans les résultats.

**Désactiver la mise en surbrillance des références**

Par défaut, quand vous sélectionnez du texte, toutes les occurrences du même texte sont automatiquement mises en surbrillance dans le document actif. Vous pouvez désactiver cette fonctionnalité en définissant **Désactiver la mise en surbrillance de la référence** sur **Vrai**.

## <a name="text-editor"></a>Éditeur de texte

**Activer l’entourage avec des accolades**

Si cette option est activée, vous pouvez entourer le texte sélectionné d’accolades en tapant « { » dans l’éditeur de texte.

**Activer l’entourage avec des parenthèses**

Si cette option est activée, vous pouvez entourer le texte sélectionné de parenthèses en tapant « ( » dans l’éditeur de texte.

## <a name="see-also"></a>Voir aussi

- [Définition des options de l’éditeur de Language-Specific](../../ide/reference/setting-language-specific-editor-options.md)
