---
title: Page Déboguer, Concepteur de projets
ms.date: 06/27/2018
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2c3e7813e5e07a0fbb8f4ebf5838c883faa0fb8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595720"
---
# <a name="debug-page-project-designer"></a>Page Déboguer, Concepteur de projets

Utilisez la page **Déboguer** du **Concepteur de projets** afin de définir des propriétés pour le comportement de débogage dans un projet Visual Basic ou C#.

Pour accéder à la page **Déboguer**, sélectionnez un nœud de projet dans **l’Explorateur de solutions**. Dans le menu **Projet**, choisissez **\<nom_projet>Propriétés**. Quand le **Concepteur de projets** s’affiche, cliquez sur l’onglet **Déboguer**.

> [!NOTE]
> Cette rubrique ne s’applique pas aux applications UWP. Consultez [Démarrer une session de débogage (VB, C#, C++ et XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) pour les applications UWP.

## <a name="configuration-and-platform"></a>Configuration et Plateforme

Les options suivantes vous permettent de sélectionner la configuration et la plateforme à afficher ou à modifier.

**Configuration**

Spécifie les paramètres de configuration à afficher ou à modifier. Les paramètres peuvent être **Debug** (valeur par défaut), **Release** ou **Toutes les configurations**.

**Plateforme**

Spécifie les paramètres de plateforme à afficher ou à modifier. Les choix possibles sont **Any CPU** (valeur par défaut), **x64** et **x86**.

## <a name="start-action"></a>Action de démarrage

**Action de démarrage** indique à l’élément de démarrer quand l’application est déboguée : le projet, un programme personnalisé, une URL ou rien. Par défaut, la valeur affectée à cette option est **Démarrer le projet**. Le paramètre **Action de démarrage** dans la page **Déboguer** détermine la valeur de la propriété `StartAction`.

**Démarrer le projet**

Sélectionnez cette option pour spécifier que le fichier exécutable (pour les projets d’application Windows et d’application console) doit être démarré quand l’application est déboguée. Cette option est activée par défaut.

**Démarrer le programme externe**

Choisissez cette option pour indiquer qu’un programme spécifique doit démarrer quand l’application est déboguée.

**Démarrer le navigateur avec l’URL**

Choisissez cette option pour spécifier qu’une URL particulière doit être accessible quand l’application est déboguée.

## <a name="start-options"></a>Options de démarrage

**Arguments de la ligne de commande**

Dans cette zone de texte, entrez les arguments de la ligne de commande à utiliser pour le débogage.

**Répertoire de travail**

Dans cette zone de texte, entrez le répertoire à partir duquel le projet sera lancé. Vous pouvez aussi cliquer sur le bouton Parcourir ( **...** ) pour sélectionner un répertoire.

**Utiliser l’ordinateur distant**

Pour déboguer l’application à partir d’un ordinateur distant, cochez cette case, puis entrez le chemin d’accès à l’ordinateur distant dans la zone de texte.

## <a name="debugger-engines"></a>Moteurs de débogage

**Activer le débogage du code natif**

Cette option spécifie si le débogage de code natif est pris en charge. Cochez cette case si vous effectuez des appels vers les objets COM ou si vous démarrez un programme personnalisé écrit en code natif qui appelle votre projet et que vous devez déboguer le code natif. Décochez cette case pour désactiver le débogage de code non managé. Cette case est décochée par défaut.

**Activer le débogage SQL Server**

Cochez ou décochez cette case pour activer ou désactiver le débogage des procédures SQL de votre application Visual Basic. Cette case est décochée par défaut.

## <a name="see-also"></a>Voir aussi

- [Présentation du débogueur](../../debugger/debugger-feature-tour.md)
- [Paramètres de projet pour des configurations de débogage C#](../../debugger/project-settings-for-csharp-debug-configurations.md)
- [Paramètres de projet pour une configuration Debug Visual Basic](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Guide pratique pour déboguer une application ClickOnce avec des autorisations restreintes](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)
- [Guide pratique pour créer et modifier des configurations](../../ide/how-to-create-and-edit-configurations.md)
