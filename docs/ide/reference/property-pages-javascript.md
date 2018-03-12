---
title: "Pages de propriétés (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 06/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- javascript.project.property.debugging.debuggertype
- javascript.project.property.debugging.requireauthentication
- javascript.project.property.outputpath
- javascript.project.property.debugging.launchapplication
- javascript.project.property.defaultlanguage
- javascript.project.property.debugging.machinename
- javascript.project.property.debugging.allowlocalnetworkloopback
ms.assetid: a05ab01f-3d5d-4675-a845-eab51807d3a3
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4e4f01a74a3246a326c1695371a303472901c9ea
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2018
---
# <a name="property-pages-javascript"></a>Pages de propriétés (JavaScript)
Les **Pages de propriétés** permettent d’accéder aux paramètres d’un projet. Vous pouvez utiliser les pages qui s’affichent dans les **Pages de propriétés** pour modifier les propriétés d’un projet.  

Pour accéder aux propriétés d’un projet, sélectionnez un nœud de projet dans l’**Explorateur de solutions**. Dans le menu **Projet**, cliquez sur **Propriétés**.  

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  

Les pages et options suivantes s’affichent dans les **Pages de propriétés**.  

## <a name="configuration-and-platform-page"></a>Page de configuration et de plateforme  
 Utilisez les options suivantes pour sélectionner la configuration et la plateforme à afficher ou à modifier.  

 **Configuration**  
 Spécifie les paramètres de configuration à afficher ou à modifier. Les valeurs sont **Debug** (valeur par défaut), **Release**, **Toutes les configurations** ou une configuration définie par l’utilisateur. Pour plus d’informations, consultez [Guide pratique pour définir des configurations Debug et Release dans Visual Studio](../../debugger/how-to-set-debug-and-release-configurations.md).  

 **Plateforme**  
 Spécifie les paramètres de plateforme à afficher ou à modifier. Les valeurs sont **Any CPU** (valeur par défaut pour les applications [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)]), **x64**, **ARM**, **x86** ou une plateforme définie par l’utilisateur. Pour plus d’informations, consultez [Guide pratique pour définir des configurations Debug et Release dans Visual Studio](../../debugger/how-to-set-debug-and-release-configurations.md).  

## <a name="general-page"></a>Page Général  
 Utilisez les options suivantes pour définir les propriétés générales du projet.  

> [!NOTE]
>  Certaines options sont disponibles seulement dans les applications UWP.  

 **Chemin de sortie**  
 Spécifie l'emplacement des fichiers de sortie pour la configuration du projet. Le chemin d'accès est relatif. Si vous entrez un chemin d'accès absolu, le chemin d'accès absolu est enregistré dans le projet. Le chemin d'accès par défaut est bin\Debug.  

 Quand vous utilisez des configurations de build simplifiées, le système de projet détermine s’il faut générer une version Debug ou une version Release. Quand vous cliquez sur **Debug**, **Démarrer le débogage** (ou que vous appuyez sur F5), la build est placée à l’emplacement de débogage, indépendamment du **Chemin de sortie** que vous spécifiez. Cependant, la commande **Générer la solution** du menu **Générer** la place à l’emplacement que vous spécifiez. Pour activer les configurations de build avancées, dans la barre de menus, choisissez **Outils**, **Options**. Dans la boîte de dialogue **Options**, développez **Projets et solutions**, sélectionnez **Général**, puis décochez la case **Afficher les configurations de build avancées**. Vous pouvez ainsi contrôler manuellement toutes les valeurs de configuration et s’il faut générer une version Debug ou Release.  

 **Langue par défaut**  
 Spécifie la langue par défaut pour le projet. L’option de langue sélectionnée dans **Horloge, langue et région** dans le Panneau de configuration spécifie la langue préférée de l’utilisateur. En spécifiant une langue par défaut pour le projet, vous garantissez que les ressources linguistiques par défaut spécifiées sont utilisées si la langue préférée de l’utilisateur ne correspond pas aux ressources linguistiques fournies dans l’application.  

## <a name="debug-page"></a>Page Déboguer  
 Utilisez les options suivantes pour définir les propriétés du comportement du débogage dans le projet.  

> [!NOTE]
>  Certaines options sont disponibles seulement dans les applications UWP.  

 **Débogueur à lancer**  
 Spécifie l'hôte par défaut pour le débogueur.  

-   Sélectionnez **Ordinateur local** pour démarrer l’application sur l’ordinateur hôte Visual Studio. Pour plus d’informations, consultez [Exécution d’applications sur un ordinateur local](../../debugger/run-windows-store-apps-on-the-local-machine.md).  

-   Sélectionnez **Simulateur** pour démarrer l’application dans le simulateur. Pour plus d’informations, consultez [Exécution d’applications dans le simulateur](../../debugger/run-windows-store-apps-in-the-simulator.md).  

-   Sélectionnez **Ordinateur distant** pour démarrer l’application sur un ordinateur distant. Pour plus d’informations sur le débogage distant, consultez [Exécution d’applications sur un ordinateur distant](../../debugger/run-windows-store-apps-on-a-remote-machine.md).  

**Lancer l’application**  
Spécifie s’il faut démarrer l’application quand vous appuyez sur F5 ou quand vous cliquez sur **Déboguer**, **Démarrer le débogage**. Sélectionnez **Oui** pour démarrer l’application ; sinon, sélectionnez **Non**. Si vous sélectionnez **Non**, vous pouvez toujours déboguer l’application si vous utilisez une autre méthode pour la démarrer.  

**Type de débogueur**  
Spécifie les types de code à déboguer. Sélectionnez **Script uniquement** pour déboguer du code JavaScript. Sélectionnez **Managé uniquement** pour déboguer du code qui est managé par le Common Language Runtime. Sélectionnez **Natif uniquement** pour déboguer du code C++. Sélectionnez **Natif avec script** pour déboguer du code C++ et JavaScript. Sélectionnez **Mixte (managé et natif)** pour déboguer à la fois le code managé et le code C++.  

**Autoriser le bouclage de réseau local**  
Spécifie si l'accès à l'adresse de bouclage IP est autorisé pour tester les applications. Sélectionnez **Oui** pour autoriser l’utilisation de l’adresse de bouclage si l’application cliente est sur le même ordinateur que celui où l’application serveur est en cours d’exécution ; sinon, sélectionnez **Non**. Cette propriété est disponible seulement si la **Débogueur à lancer** est définie sur **Ordinateur distant**.  

**Nom de l’ordinateur**  
Spécifie le nom de l'ordinateur distant pour héberger le débogueur. Cette propriété est disponible seulement si la propriété **Débogueur à lancer** est définie sur **Ordinateur distant**.  

**Exiger une authentification**  
Spécifie si l'ordinateur distant requiert l'authentification. Cette propriété est disponible seulement si la propriété **Débogueur à lancer** est définie sur **Ordinateur distant**.
