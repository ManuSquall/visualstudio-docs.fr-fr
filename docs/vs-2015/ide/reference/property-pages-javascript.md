---
title: Pages de propriétés (JavaScript) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- javascript.project.property.debugging.debuggertype
- javascript.project.property.debugging.requireauthentication
- javascript.project.property.outputpath
- javascript.project.property.debugging.launchapplication
- javascript.project.property.defaultlanguage
- javascript.project.property.debugging.machinename
- javascript.project.property.debugging.allowlocalnetworkloopback
ms.assetid: a05ab01f-3d5d-4675-a845-eab51807d3a3
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9fa22a4ed52c3e0a1afdda0105716c0de9b3316
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851810"
---
# <a name="property-pages-javascript"></a>Pages de propriétés (JavaScript)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Les **Pages de propriétés** permettent d’accéder aux paramètres d’un projet. Vous pouvez utiliser les pages qui s’affichent dans les **Pages de propriétés** pour modifier les propriétés d’un projet.

 Pour accéder aux propriétés d’un projet, sélectionnez un nœud de projet dans l’**Explorateur de solutions**. Dans le menu **Projet**, cliquez sur **Propriétés**.

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

 Les pages et options suivantes s’affichent dans les **Pages de propriétés**.

## <a name="configuration-and-platform-page"></a>Page de configuration et de plateforme
 Utilisez les options suivantes pour sélectionner la configuration et la plateforme à afficher ou à modifier.

 **Configuration** de Spécifie les paramètres de configuration à afficher ou à modifier. Les valeurs sont **Debug** (valeur par défaut), **Release**, **Toutes les configurations** ou une configuration définie par l’utilisateur. Pour plus d’informations, consultez [Configurations de projet Debug et Release](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **Plateforme** Spécifie les paramètres de plateforme à afficher ou à modifier. Les valeurs sont **Any CPU** (valeur par défaut pour les applications [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]), **x64**, **ARM**, **x86** ou une plateforme définie par l’utilisateur. Pour plus d’informations, consultez [Configurations de projet Debug et Release](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

## <a name="general-page"></a>page Général
 Utilisez les options suivantes pour définir les propriétés générales du projet.

> [!NOTE]
> Certaines options sont disponibles seulement dans les applications du Windows Store.

 **Chemin de sortie** Spécifie l’emplacement des fichiers de sortie pour la configuration du projet. Le chemin d'accès est relatif. Si vous entrez un chemin d'accès absolu, le chemin d'accès absolu est enregistré dans le projet. Le chemin d'accès par défaut est bin\Debug.

 Quand vous utilisez des configurations de build simplifiées, le système de projet détermine s’il faut générer une version Debug ou une version Release. Quand vous cliquez sur **Debug**, **Démarrer le débogage** (ou que vous appuyez sur F5), la build est placée à l’emplacement de débogage, indépendamment du **Chemin de sortie** que vous spécifiez. Cependant, la commande **Générer la solution** du menu **Générer** la place à l’emplacement que vous spécifiez. Pour activer les configurations de build avancées, dans la barre de menus, choisissez **Outils**, **Options**. Dans la boîte de dialogue **Options**, développez **Projets et solutions**, sélectionnez **Général**, puis décochez la case **Afficher les configurations de build avancées**. Vous pouvez ainsi contrôler manuellement toutes les valeurs de configuration et s’il faut générer une version Debug ou Release. Pour plus d’informations, consultez [plume : général, projets et solutions, boîte de dialogue Options](https://msdn.microsoft.com/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).

 **Langue par défaut** Spécifie la langue par défaut du projet. L’option de langue sélectionnée dans **Horloge, langue et région** dans le Panneau de configuration spécifie la langue préférée de l’utilisateur. En spécifiant une langue par défaut pour le projet, vous vous assurez que les ressources linguistiques par défaut spécifiées sont utilisées si la langue préférée de l'utilisateur ne correspond pas aux ressources linguistiques fournies dans l'application.

## <a name="debug-page"></a>Page Déboguer
 Utilisez les options suivantes pour définir les propriétés du comportement du débogage dans le projet.

> [!NOTE]
> Certaines options sont disponibles seulement dans les applications du Windows Store.

 **Débogueur à lancer** Spécifie l’hôte par défaut pour le débogueur.

- Sélectionnez **Ordinateur local** pour démarrer l’application sur l’ordinateur hôte Visual Studio. Pour plus d’informations, consultez [Exécution d’applications sur un ordinateur local](https://msdn.microsoft.com/library/windows/apps/hh441483(v=VS.85).aspx).

- Sélectionnez **Simulateur** pour démarrer l’application dans le simulateur. Pour plus d’informations, consultez [Exécution d’applications dans le simulateur](https://msdn.microsoft.com/library/windows/apps/hh441475(v=VS.85).aspx).

- Sélectionnez **Ordinateur distant** pour démarrer l’application sur un ordinateur distant. Pour plus d’informations sur le débogage distant, consultez [Exécution d’applications sur un ordinateur distant](https://msdn.microsoft.com/library/windows/apps/hh441469(v=VS.85).aspx).

  **Lancer l’application** Spécifie si l’application doit être démarrée lorsque vous appuyez sur F5 ou que vous cliquez sur **Déboguer**, **Démarrer le débogage**. Sélectionnez **Oui** pour démarrer l’application ; sinon, sélectionnez **Non**. Si vous sélectionnez **Non**, vous pouvez toujours déboguer l’application si vous utilisez une autre méthode pour la démarrer.

  **Type de débogueur** Spécifie les types de code à déboguer. Sélectionnez **Script uniquement** pour déboguer du code JavaScript. Sélectionnez **Managé uniquement** pour déboguer du code qui est managé par le Common Language Runtime. Sélectionnez **Natif uniquement** pour déboguer du code C++. Sélectionnez **Natif avec script** pour déboguer du code C++ et JavaScript. Sélectionnez **Mixte (managé et natif)** pour déboguer à la fois le code managé et le code C++.

  **Autoriser le bouclage de réseau local** Spécifie si l’accès à l’adresse de bouclage IP est autorisé pour le test d’application. Sélectionnez **Oui** pour autoriser l’utilisation de l’adresse de bouclage si l’application cliente est sur le même ordinateur que celui où l’application serveur est en cours d’exécution ; sinon, sélectionnez **Non**. Cette propriété est disponible seulement si la **Débogueur à lancer** est définie sur **Ordinateur distant**.

  **Nom** de l’ordinateur Spécifie le nom de l’ordinateur distant pour héberger le débogueur. Cette propriété est disponible seulement si la propriété **Débogueur à lancer** est définie sur **Ordinateur distant**.

  **Exiger une authentification** Spécifie si l’ordinateur distant requiert une authentification. Cette propriété est disponible seulement si la propriété **Débogueur à lancer** est définie sur **Ordinateur distant**.
