---
title: "Pages de propri&#233;t&#233;s (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "javascript.project.property.debugging.debuggertype"
  - "javascript.project.property.debugging.requireauthentication"
  - "javascript.project.property.outputpath"
  - "javascript.project.property.debugging.launchapplication"
  - "javascript.project.property.defaultlanguage"
  - "javascript.project.property.debugging.machinename"
  - "javascript.project.property.debugging.allowlocalnetworkloopback"
ms.assetid: a05ab01f-3d5d-4675-a845-eab51807d3a3
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Pages de propri&#233;t&#233;s (JavaScript)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les **Pages de propriétés** fournissent un accès aux paramètres du projet.  Vous pouvez utiliser les pages qui apparaissent dans les **Pages de propriétés** pour modifier les propriétés du projet.  
  
 Pour accéder aux propriétés du projet, sélectionnez un nœud du projet dans l'**Explorateur de solutions**.  Dans le menu **Projet**, cliquez sur **Propriétés**.  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
 Les pages et les options suivantes apparaissent dans les **Pages de propriétés**.  
  
## Page de configuration et de plateforme  
 Utilisez les options suivantes pour sélectionner la configuration et la plateforme à afficher ou à modifier.  
  
 **Configuration**  
 Spécifie les paramètres de configuration à afficher ou à modifier.  Les valeurs sont **Debug** \(par défaut\), **Release**, **Toutes les configurations** ou une configuration définie par l'utilisateur.  Pour plus d'informations, consultez [Debug and Release Project Configurations](http://msdn.microsoft.com/fr-fr/0440b300-0614-4511-901a-105b771b236e).  
  
 **Plateforme**  
 Spécifie les paramètres de plateforme à afficher ou à modifier.  Les valeurs sont **Tout processeur** \(valeur par défaut pour les applications du [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)]\), **x64**, **ARM**, **x 86** ou une plateforme définie par l'utilisateur.  Pour plus d'informations, consultez [Debug and Release Project Configurations](http://msdn.microsoft.com/fr-fr/0440b300-0614-4511-901a-105b771b236e).  
  
## Page Général  
 Utilisez les options suivantes pour définir les propriétés générales du projet.  
  
> [!NOTE]
>  Certaines options sont disponibles seulement dans les applications du Windows Store.  
  
 **Chemin de sortie**  
 Spécifie l'emplacement des fichiers de sortie pour la configuration du projet.  Le chemin d'accès est relatif. Si vous entrez un chemin d'accès absolu, le chemin d'accès absolu est enregistré dans le projet.  Le chemin d'accès par défaut est bin\\Debug.  
  
 Quand vous utilisez des configurations de build simplifiées, le système de projet détermine s'il faut générer une version Debug ou une version Release.  Quand vous cliquez sur **Debug**, **Démarrer le débogage** \(ou que vous appuyez sur F5\), la build est placée à l'emplacement de débogage, indépendamment du **Chemin de sortie** que vous spécifiez.  Cependant, la commande **Générer la solution** du menu **Générer** la place à l'emplacement que vous spécifiez.  Pour activer les configurations de build avancées, dans la barre de menus, choisissez **Outils**, **Options**.  Dans la boîte de dialogue **Options**, développez **Projets et solutions**, sélectionnez **Général**, puis décochez la case **Afficher les configurations de build avancées**.  Vous pouvez ainsi contrôler manuellement toutes les valeurs de configuration et s'il faut générer une version Debug ou Release.  Pour plus d'informations, consultez [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/fr-fr/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
 **Langue par défaut**  
 Spécifie la langue par défaut pour le projet.  L'option de langue sélectionnée dans **Horloge, langue et région** dans le Panneau de configuration spécifie la langue préférée de l'utilisateur.  En spécifiant une langue par défaut pour le projet, vous vous assurez que les ressources linguistiques par défaut spécifiées sont utilisées si la langue préférée de l'utilisateur ne correspond pas aux ressources linguistiques fournies dans l'application.  
  
## Page Déboguer  
 Utilisez les options suivantes pour définir les propriétés du comportement du débogage dans le projet.  
  
> [!NOTE]
>  Certaines options sont disponibles seulement dans les applications du Windows Store.  
  
 **Débogueur à lancer**  
 Spécifie l'hôte par défaut pour le débogueur.  
  
-   Sélectionnez **Ordinateur local** pour démarrer l'application sur l'ordinateur hôte de Visual Studio.  Pour plus d'informations, consultez [Exécution d'applications sur l'ordinateur local](http://go.microsoft.com/fwlink/?LinkId=234912).  
  
-   Sélectionnez **Simulateur** pour démarrer l'application dans le simulateur.  Pour plus d'informations, consultez [Exécution d'applications dans le simulateur](http://go.microsoft.com/fwlink/?LinkId=234913).  
  
-   Sélectionnez **Ordinateur distant** pour démarrer l'application sur un ordinateur distant.  Pour plus d'informations, consultez [Exécution d'applications sur un ordinateur distant](http://go.microsoft.com/fwlink/?LinkId=234914).  
  
 **Lancer l'application**  
 Spécifie s'il faut démarrer l'application quand vous appuyez sur F5 ou quand vous cliquez sur **Déboguer**, **Démarrer le débogage**.  Sélectionnez **Oui** pour démarrer l'application ; sinon, sélectionnez **Non**.  Si vous sélectionnez **Non**, vous pouvez néanmoins toujours déboguer l'application si vous utilisez une méthode différente pour la démarrer.  
  
 **Type de débogueur**  
 Spécifie les types de code à déboguer.  Sélectionnez **Script uniquement** pour déboguer le code JavaScript.  Sélectionnez **Managé uniquement** pour déboguer le code qui est géré par le common language runtime.  Sélectionnez **Natif uniquement** pour déboguer le code C\+\+.  Sélectionnez **natif avec Script** pour déboguer C\+\+ et JavaScript.  Sélectionnez **Mixte \(managé et natif\)** pour déboguer le code managé et le code C\+\+.  
  
 **Autoriser le bouclage de réseau local**  
 Spécifie si l'accès à l'adresse de bouclage IP est autorisé pour tester les applications.  Sélectionnez **Oui** pour autoriser l'utilisation de l'adresse de bouclage si l'application cliente est sur le même ordinateur que celui où l'application serveur s'exécute ; sinon, sélectionnez **Non**.  Cette propriété est disponible seulement si la propriété **Débogueur à lancer** est définie sur **Ordinateur distant**.  
  
 **Nom de l'ordinateur**  
 Spécifie le nom de l'ordinateur distant pour héberger le débogueur.  Cette propriété est disponible seulement si la propriété **Débogueur à lancer** est définie sur **Ordinateur distant**.  
  
 **Exiger une authentification**  
 Spécifie si l'ordinateur distant requiert l'authentification.  Cette propriété est disponible seulement si la propriété **Débogueur à lancer** est définie sur **Ordinateur distant**.