---
title: Page Déboguer, Concepteur de projets | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 006662d7c07ba0498fff4617eca3fdc7c631d37b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660783"
---
# <a name="debug-page-project-designer"></a>Page Déboguer, Concepteur de projets
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!WARNING]
> Cette rubrique ne s'applique pas aux applications Windows Store. Consultez [Démarrer une session de débogage (VB, C#, C++ et XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) dans le Centre de développement Windows.

 Utilisez la page **Déboguer** du **Concepteur de projets** afin de définir des propriétés pour le comportement de débogage dans un projet Visual Basic ou C#.

 Pour accéder à la page **Déboguer**, sélectionnez un nœud de projet dans **l’Explorateur de solutions**. Dans le menu **projet** , choisissez _ProjectName_**Propriétés**ProjectName. Quand le **Concepteur de projets** s’affiche, cliquez sur l’onglet **Déboguer**.

## <a name="configuration-and-platform"></a>Configuration et Plateforme
 Les options suivantes vous permettent de sélectionner la configuration et la plateforme à afficher ou à modifier.

 **Configuration** Spécifie les paramètres de configuration à afficher ou à modifier. Les paramètres peuvent être **Debug** (valeur par défaut), **Release** ou **Toutes les configurations**. Pour plus d’informations, consultez [Configurations de projet Debug et Release](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **Plateforme** Spécifie les paramètres de plateforme à afficher ou à modifier. Les choix possibles sont **Any CPU** (valeur par défaut), **x64** et **x86**. Pour plus d’informations, consultez [Configurations de projet Debug et Release](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

## <a name="start-action"></a>Action de démarrage
 **Action de démarrage** indique l’élément à démarrer lors du débogage de l’application : le projet, un programme personnalisé, une URL ou rien. Par défaut, la valeur affectée à cette option est **Démarrer le projet**. Le paramètre **Action de démarrage** dans la page **Déboguer** détermine la valeur de la propriété `StartAction`.

 **Démarrer le projet** Choisissez cette option pour spécifier que le fichier exécutable (pour les projets d’application Windows et d’application console) doit être démarré lorsque l’application est déboguée. Cette option est activée par défaut.

 **Démarrer le programme externe** Choisissez cette option pour spécifier qu’un programme spécifique doit être démarré lors du débogage de l’application.

 **Démarrer le navigateur avec l’URL** Choisissez cette option pour spécifier qu’une URL particulière doit être accessible lors du débogage de l’application.

## <a name="start-options"></a>Options de démarrage
 **Arguments de ligne de commande** Dans cette zone de texte, entrez les arguments de ligne de commande à utiliser pour le débogage.

 **Répertoire de travail** Dans cette zone de texte, entrez le répertoire à partir duquel le projet sera lancé. Vous pouvez aussi cliquer sur le bouton Parcourir (**...**) pour sélectionner un répertoire.

 **Utiliser l’ordinateur distant** Pour déboguer l’application à partir d’un ordinateur distant, activez cette case à cocher, puis entrez le chemin d’accès à l’ordinateur distant dans la zone de texte.

## <a name="enable-debuggers"></a>Activer les débogueurs
 **Activer le débogage de code non managé** Cette option spécifie si le débogage du code natif est pris en charge. Cochez cette case si vous effectuez des appels vers les objets COM ou si vous démarrez un programme personnalisé écrit en code natif qui appelle votre projet et que vous devez déboguer le code natif. Décochez cette case pour désactiver le débogage de code non managé. Cette case à cocher est désactivée par défaut.

 **Activer le débogage SQL Server** Activez ou désactivez cette case à cocher pour activer ou désactiver le débogage de procédures SQL à partir de votre application Visual Basic. Cette case à cocher est désactivée par défaut.

 **Activer le processus d’hébergement Visual Studio** Activez cette case à cocher pour activer le processus d’hébergement Visual Studio. Cette case à cocher est activée par défaut. Pour plus d’informations, consultez [Processus d’hébergement (vshost.exe)](../../ide/hosting-process-vshost-exe.md).

 Pour déboguer dans une zone de sécurité, vous devez activer cette option et **Déboguer cette application à l’aide du jeu d’autorisations sélectionné** dans la [boîte de dialogue Paramètres de sécurité avancés](../../ide/reference/advanced-security-settings-dialog-box.md).

## <a name="see-also"></a>Voir aussi
 [Débogage dans](../../debugger/debugging-in-visual-studio.md) [les paramètres de projet Visual Studio pour les configurations de débogage C#](../../debugger/project-settings-for-csharp-debug-configurations.md) [paramètres du projet pour une configuration](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md) de débogage de Visual Basic [gestion des propriétés de débogage](https://msdn.microsoft.com/92474d16-e7fe-4fac-9287-6bd6b3a7eb68) [Comment : déboguer une application ClickOnce avec des autorisations restreintes](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md) [Comment : créer et modifier des configurations](../../ide/how-to-create-and-edit-configurations.md)
