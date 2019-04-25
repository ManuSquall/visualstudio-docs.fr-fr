---
title: Journal des modifications (Visual Studio Tools pour Unity, Windows) | Microsoft Docs
ms.custom: ''
ms.date: 04/02/2019
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: a635ca7369470788f0813f6e246767b64f6af445
ms.sourcegitcommit: 0a2fdc23faee77187e10a1c19665ba5a1ac68e72
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/10/2019
ms.locfileid: "59477663"
---
# <a name="change-log-visual-studio-tools-for-unity-windows"></a>Journal des modifications (Outils Visual Studio pour Unity, Windows)
Journal des modifications Visual Studio Tools pour Unity

## <a name="4005"></a>4.0.0.5
 Publication : 27 février 2019

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Intégration :**

    -   Correction de la détection de version de Visual Studio avec le package d’installation.

    -   Suppression des assemblys inutilisés du package d’installation.

## <a name="4004"></a>4.0.0.4
 Publication : 13 février 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Intégration :**

    -   Prise en charge de la détection des processus Unity lors de l’installation et meilleure gestion du verrouillage de fichier par le moteur d’installation.
    
    -   Mise à jour de l’API ScriptableObject.

## <a name="4003"></a>4.0.0.3
 Publication : 31 janvier 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Génération de projet :**

    -   Suppression des avertissements générés par les champs publics et sérialisés. Nous avons supprimé automatiquement les avertissements du compilateur CS0649 et IDE0051 dans les projets Unity qui créaient ces messages.

-   **Intégration :**

    -   Amélioration de l’expérience utilisateur pour l’affichage des instances d’éditeur et de lecteur Unity (fenêtres redimensionnables, avec marges uniformes et poignée de redimensionnement). Ajout d’informations sur l’identificateur de processus pour les éditeurs Unity.
    
    -   Mise à jour de l’API MonoBehaviour.
    
-   **Évaluation :**

    -   Prise en charge des fonctions locales.
    
    -   Prise en charge des pseudo-variables (identificateurs d’exception et d’objet).

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Intégration :**

    -   Correction d’un problème avec les thèmes et les images moniker.

    -   Restriction des écritures à la fenêtre Sortie pendant le débogage, lors de l’actualisation automatique de la base de données de ressources.

    -   Correction des délais de l’interface utilisateur lors du filtrage avec l’Assistant MonoBehaviour.
    
-   **Débogueur :**

    -   Correction de la lecture des attributs personnalisés sur les arguments nommés avec d’anciennes versions des protocoles.

## <a name="4002"></a>4.0.0.2
 Publication : 23 janvier 2019

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Intégration :**

    -   Correction de la génération de builds expérimentales.

    -   Correction de la gestion des événements du fichier projet afin de réduire la sollicitation des threads d’interface utilisateur.

    -   Correction du fournisseur de complétion avec les modifications de texte par lots.
    
-   **Débogueur :**

    -   Correction de l’affichage des messages de débogage utilisateur du débogueur attaché.

## <a name="4001"></a>4.0.0.1
 Publication : 10 décembre 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Évaluation :**

    -   Remplacement de NRefactory par Roslyn pour l’évaluation des expressions.

    -   Prise en charge des pointeurs : déréférencement, cast et arithmétique (Unity 2018.2 ou version ultérieure et nouveau runtime requis).

    -   Prise en charge de l’affichage des pointeurs sous forme de tableau (comme en C++). Prenez une expression de pointeur, puis ajoutez-y une virgule et le nombre d’éléments à afficher.

    -   Prise en charge des constructions asynchrones.

-   **Intégration :**
    
    -   Prise en charge de l’actualisation automatique de la base de données de la ressource Unity à l’enregistrement. Activée par défaut, cette fonctionnalité déclenche une recompilation côté Unity lors de l’enregistrement d’un script dans Visual Studio. Vous pouvez la désactiver dans Tools\Options\Tools for Unity\Refresh Unity’s AssetDatabase on save.

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Intégration :**

    -   Correction de l’activation de pont lorsque Visual Studio n’est pas sélectionné comme éditeur externe par défaut.

    -   Correction de l’évaluation des expressions mal formées ou non prises en charge.

## <a name="4000"></a>4.0.0.0
 Publication : 4 décembre 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Intégration :**

    -   Ajout de la prise en charge de Visual Studio 2019 (vous avez besoin d’au moins Unity 2018.3 pour pouvoir utiliser Visual Studio 2019 comme éditeur de script externe).

    -   Adoption du catalogue et du service d’images Visual Studio, avec prise en charge complète de la mise à l’échelle HDPI et des thèmes et des images non pixellisés.

### <a name="deprecated-features"></a>Fonctionnalités dépréciées

-   **Intégration :**

    -   À l’avenir, les Outils Visual Studio pour Unity prendront seulement en charge Unity 5.2 et les versions ultérieures (avec intégration Visual Studio prédéfinie de Unity).

    -   À l’avenir, les Outils Visual Studio pour Unity prendront seulement en charge Visual Studio 2015 et les versions ultérieures.

    -   Suppression de l’ancien service de langage, de l’ancienne liste d’erreurs et de l’ancienne barre d’état.
    
    -   Suppression de l’Assistant rapide MonoBehaviour (prise en charge IntelliSense dédiée).

## <a name="3903"></a>3.9.0.3
 Publication : 28 novembre 2018

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Intégration :**

    -   Correction des problèmes intellisense et de rechargement de projet lors de l’ajout ou de la suppression de scripts situés dans le tout premier projet.

## <a name="3902"></a>3.9.0.2
 Publication : 19 novembre 2018

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Débogueur :**

    -   Correction d’un blocage dans la bibliothèque utilisée pour communiquer avec le moteur de débogage de Unity, à cause duquel Visual Studio ou Unity se figeait, en particulier lorsque l’on sélectionnait « Attacher à Unity » ou que l’on redémarrait le jeu.

## <a name="3901"></a>3.9.0.1
 Publication : 15 novembre 2018

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Intégration :**

    -   Correction du problème d’activation du plug-in Unity lorsqu’un autre éditeur par défaut était sélectionné.

## <a name="3900"></a>3.9.0.0
 Publication : 13 novembre 2018

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Génération de projet :**

    -   Restauration de la solution de contournement d’un bogue de performances Unity corrigé par Unity.

## <a name="3807"></a>3.8.0.7
 Publiée le 20 septembre 2018

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Débogueur :**

    -   (Reporté depuis 3.9.0.2) Correction d’un blocage dans la bibliothèque utilisée pour communiquer avec le moteur de débogage de Unity, à cause duquel Visual Studio ou Unity se figeait, en particulier lorsque l’on sélectionnait « Attacher à Unity » ou que l’on redémarrait le jeu.

## <a name="3806"></a>3.8.0.6
 Publication : 27 août 2018

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Intégration :**

    -   Correction du rechargement des projets et de la solution.

## <a name="3805"></a>3.8.0.5
 Publication : 20 août 2018

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Intégration :**

    -   Correction de la suppression de l’abonnement de surveillance des projets.

## <a name="3804"></a>3.8.0.4
 Publication : 14 août 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Évaluation :**

    -   Ajout de la prise en charge des valeurs de pointeurs.

    -   Ajout de la prise en charge des méthodes génériques.

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Intégration :**

    -   Rechargement intelligent quand des changements sont apportés à plusieurs projets.

## <a name="3803"></a>3.8.0.3
 Publiée le 24 juillet 2018

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Génération de projet :**

    -   (Reporté depuis 3.9.0.0) Restauration de la solution de contournement d’un bogue de performances Unity corrigé par Unity.

## <a name="3802"></a>3.8.0.2
 Publication : 7 juillet 2018

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Génération de projet :**

    -   Solution de contournement temporaire pour un bogue de performances Unity : mise en cache de MonoIslands lors de la génération des projets.

## <a name="3801"></a>3.8.0.1
 Publiée le 26 juin 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Débogage :**

    -   Ajout de la prise en charge des commandes UserLog et UserBreak.

    -   Ajout de la prise en charge du chargement différé (optimisation de la charge réseau et de la latence de réponse du débogueur).

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Évaluation :**

    -   Amélioration de l’évaluation des expressions d’opérateurs binaires et de la recherche de méthodes.

## <a name="3800"></a>3.8.0.0
 Publication : 30 mai 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Débogage :**

    -   Ajout de la prise en charge de l’affichage des variables dans les constructions asynchrones.

    -   Ajout de la prise en charge du traitement des types imbriqués durant la définition des points d’arrêt, pour empêcher les avertissements liés aux constructions du compilateur.

-   **Intégration :**

    -   Ajout de la prise en charge des grammaires textmate pour les nuanceurs (la charge de travail C++ n’est plus nécessaire pour la coloration du code Shader).

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Génération de projet :**

    -   Ne convertissez plus un fichier pdb portable en mdb lors de l’utilisation du nouveau runtime Unity.

## <a name="3701"></a>3.7.0.1
 Publication : 7 mai 2018

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Programme d’installation :**

    -   Correction d’un problème de dépendance fixe lors de l’utilisation de builds expérimentales.

## <a name="3700"></a>3.7.0.0
 Publication : 7 mai 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Débogage :**

    -   Ajout de la prise en charge du débogage orchestré (débogage de plusieurs lecteurs/éditeurs dans la même session Visual Studio).

    -   Ajout de la prise en charge du débogage du lecteur USB Android.

    -   Ajout de la prise en charge du débogage du lecteur UWP/IL2CPP.

-   **Évaluation :**

    -   Ajout de la prise en charge des spécificateurs hexadécimaux.

    -   Amélioration de l’évaluation de la fenêtre Espion.

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Intégration :**

    -   Correction de l’utilisation des paramètres d’exception.

-   **Génération de projet :**

    -   Exclusion de la génération des unités de compilation du gestionnaire de package.

## <a name="3605"></a>3.6.0.5
 Publication : 13 mars 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Génération de projet :**

    -   Ajout de la prise en charge du nouveau générateur de projet dans Unity 2018.1.

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Intégration :**

    -   Correction de la gestion des états endommagés avec les projets personnalisés.

-   **Débogueur :**

    -   Résolution de la définition de l’instruction suivante.

## <a name="3604"></a>3.6.0.4
 Publiée le 5 mars 2018

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Génération de projet :**

    -   Détection de la version mono fixe.

-   **Intégration :**

    -   Résolution des problèmes de synchronisation avec 2018.1 et activation du plug-in.

## <a name="3603"></a>3.6.0.3
 Publication : 23 février 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Génération de projet :**

    -   Ajout de la prise en charge de .NET Standard.

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Génération de projet :**

    -   Correction de la détection de framework cible fixe Unity.

-   **Débogueur :**

    -   Correction de l’arrêt sur les exceptions levées en dehors du code utilisateur.

## <a name="3602"></a>3.6.0.2
 Publication : 7 février 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Intégration :**

    -   Mise à jour de la surface de l’API UnityMessage pour 2017.3.

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Intégration :**

    -   Recharger uniquement les projets avec une modification externe (avec limitation).

## <a name="3601"></a>3.6.0.1
 Publiée le 24 janvier 2018

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Intégration :**

    -   Correction du problème de conversion automatique des symboles de débogage pdb-mdb.

    -   Correction de l’appel indirect à EditorPrefs.GetBool affectant l’inspecteur lors de la tentative de modifier la taille du tableau.

## <a name="3600"></a>3.6.0.0
 Publication : 10 janvier 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Génération de projet :**

    -   Prise en charge ajoutée du modèle de référence MonoIsland 2018.1.

-   **Évaluation :**

    -   Prise en charge ajoutée de l’identificateur $exception.

-   **Débogueur :**

    -   Prise en charge ajoutée des attributs DebuggerHidden/DebuggerStepThrough avec le nouveau runtime Unity.

-   **Assistants :**

    -   Présentation de la version « la plus récente » pour les Assistants.

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Génération de projet :**

    -   Correction du calcul GUID de projet pour les projets de lecteur.

-   **Débogueur :**

    -   Correction d’une concurrence dans la gestion des événements d’arrêt.

-   **Assistants :**

    -   Actualiser le contexte roslyn avant d’insérer la méthode.

## <a name="3503"></a>3.5.0.3
 Publication : 9 janvier 2018

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Intégration :**

    -   Correction du problème de conversion automatique des symboles de débogage pdb-mdb.

## <a name="3502"></a>3.5.0.2
 Publication : 4 décembre 2017

### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Intégration :**

    -   Les projets Unity sont désormais automatiquement rechargés dans Visual Studio quand vous ajoutez ou supprimez un script Unity.

-   **Débogueur :**

    -   Ajout d’une option pour utiliser le débogueur Mono partagé par Xamarin et Visual Studio pour Mac afin de déboguer l’éditeur Unity.

    -   Ajout de la prise en charge des fichiers de symboles de débogage portables.

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Intégration :**

    -   Correction des dépendances du programme d’installation.

    -   Correction du problème qui empêchait l’affichage du menu d’aide dans l’API Unity.

-   **Génération de projet :**

    -   Correction de la génération d’un projet Player dans un jeu UWP avec le backend IL2CPP/.NET 4.6.

    -   Correction du problème de l’ajout d’une extension .dll supplémentaire au nom du fichier d’assembly.

    -   Correction du problème de l’utilisation d’un niveau de compatibilité d’une API de projet spécifique au lieu du niveau général.

    -   Ne forcez pas l’indicateur Unity AllowAttachedDebuggingOfEditor, car la valeur par défaut est maintenant true.

## <a name="3402"></a>3.4.0.2
 Publication : 19 septembre 2017

### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Génération de projet :**

    -   Ajout de la prise en charge des unités de compilation assembly.json.

    -   Arrêt de la copie des assemblys Unity dans le dossier du projet.

-   **Débogueur :**

    -   Ajout de la prise en charge de la définition de l’instruction suivante avec le nouveau runtime Unity.

    -   Ajout de la prise en charge du type Decimal avec le nouveau runtime Unity.

    -   Ajout de la prise en charge des conversions implicites/explicites.

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Évaluation :**

    -   Correction de la création d’un tableau avec une taille implicite.

    -   Correction des éléments générés par le compilateur avec des variables locales.

-   **Génération de projet :**

    -   Correction de la référence à Microsoft.CSharp fixe pour le niveau d’API 4.6.

## <a name="3302"></a>3.3.0.2
 Publication : 15 août 2017

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Génération de projet :**

    -   Correction du problème de la génération de solutions Visual Studio sur Unity 5.5 et antérieur.

## <a name="3300"></a>3.3.0.0
 Publication : 14 août 2017

### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Évaluation :**

    -   Ajout de la prise en charge de la création de structs avec le nouveau runtime Unity.

    -   Ajout de la prise en charge minimaliste des pointeurs.

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Évaluation :**

    -   Correction de l’appel de méthode sur les primitives.

    -   Correction de l’évaluation des champs contenant des types marqués avec BeforeFieldInit.

    -   Correction des appels non pris en charge avec les opérateurs binaires (soustraction).

    -   Correction des problèmes liés à l’ajout d’éléments à Visual Studio Watch.

-   **Génération de projet :**

    -   Correction des références de nom d’assembly avec des fichiers mcs.rsp.

    -   Correction des définitions avec des niveaux d’API.

## <a name="3200"></a>3.2.0.0
 Publication : 10 mai 2017

### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Programme d’installation :**

    -   Ajout de la prise en charge du nettoyage du cache MEF.

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Éditeur de code :**

    -   Correction de la classification/exécution avec des attributs personnalisés.

    -   Correction du scintillement avec les messages Unity.

## <a name="3100"></a>3.1.0.0
 Publication : 7 avril 2017

### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Débogueur :**

    -   Ajout de la prise en charge du nouveau runtime Unity (avec compatibilité avec .NET 4.6 / C# 6).

-   **Génération de projet :**

    -   Ajout de la prise en charge du profil .NET 4.6.

    -   Ajout de la prise en charge des fichiers mcs.rsp.

    -   Activation de l’option du compilateur Autoriser le code unsafe quand Unity 5.6 est utilisé.

    -   Ajout de la prise en charge de la création de projet « Lecteur » lors de l’utilisation de la plateforme Windows Store et d’un back-end il2cpp.

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Éditeur de code :**

    -   Position du signe insertion fixe après l’insertion d’une méthode avec la saisie semi-automatique.

-   **Génération de projet :**

    -   Suppression du post-traitement de version d’assembly.

## <a name="3001"></a>3.0.0.1
 Publication : 7 mars 2017

### <a name="this-version-includes-all-new-features-and-bug-fixes-introduced-with-28x-series"></a>Cette version inclut toutes les nouvelles fonctionnalités et les correctifs de bogues introduits avec la série 2.8.x.

## <a name="2820---30-preview-3"></a>2.8.2.0 - 3.0 préversion 3
 Publication : 25 janvier 2017

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Génération de projet :**

    -   Correction d’une régression où les projets Plug-ins étaient référencés à deux reprises, d’abord comme DLL binaire, puis comme projet de référence.

## <a name="2810---30-preview-2"></a>2.8.1.0 - 3.0 préversion 2
 Publication : 23 janvier 2017

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Éditeur de code :**

    -   Résolution d’un incident lié à une déclaration d’attribut sans accolade de fin.

-   **Débogueur :**

    -   Correction d’un problème de points d’arrêt de fonction avec les coroutines dans le nouveau compilateur/runtime Unity.

    -   Ajout d’un avertissement en cas d’impossibilité de liaison d’un point d’arrêt (quand l’emplacement source correspondant est introuvable).

-   **Génération de projet :**

    -   Correction d’un problème de génération de fichier csproj avec des caractères spéciaux/localisés.

    -   Correction d’un problème de références situées hors de Assets, par exemple Library (Facebook SDK).

-   **Divers :**

    -   Ajout d’une vérification pour empêcher Unity de s’exécuter au moment de l’installation ou de la désinstallation.

    -   Passage à https pour cibler la documentation Unity distante.

## <a name="2800---30-preview"></a>2.8.0.0 - 3.0 préversion
 Publication : 17 novembre 2016

### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Général :**

    -   Ajout de la prise en charge du programme d’installation de Visual Studio 2017.

    -   Ajout de la prise en charge d’extensions Visual Studio 2017.

    -   Ajout de la prise en charge de la localisation.

-   **Éditeur de code :**

    -   Ajout d’IntelliSense C# pour les messages Unity.

    -   Ajout de la coloration de code C# pour les messages Unity.

-   **Débogueur :**

    -   Ajout de la prise en charge des expressions `is`, `as`, direct cast, `default`, `new`.

    -   Ajout de la prise en charge des expressions de concaténation de chaîne.

    -   Ajout de la prise en charge de l’affichage hexadécimal des valeurs entières.

    -   Ajout de la prise en charge de la création de variables temporaires (instructions).

    -   Ajout de la prise en charge des conversions de primitives implicites.

    -   Ajout de messages d’erreur plus clairs quand un type est attendu ou introuvable.

-   **Génération de projet :**

    -   Suppression du suffixe CSharp des noms de projets.

    -   Suppression de la référence à un fichier de cibles msbuild à l’échelle du système.

-   **Assistants :**

    -   Ajout de la prise en charge des messages Unity dans les types non Behaviour comme Editor ou EditorWindow.

    -   Passage à Roslyn pour injecter et mettre en forme les messages Unity.

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Débogueur :**

    -   Résolution d’un bogue qui provoque l’arrêt brutal d’Unity durant l’évaluation des types génériques.

    -   Correction d’un problème de gestion des types Nullable.

    -   Correction d’un problème de gestion des enums.

    -   Correction d’un problème de gestion des types de membre imbriqués.

    -   Correction d’un problème d’accès à l’indexeur de collection.

    -   Correction d’un problème de prise en charge du débogage des frames de l’itérateur avec le nouveau compilateur C#.

-   **Génération de projet :**

    -   Résolution d’un bogue qui empêche la compilation quand Unity Web Player est ciblé.

    -   Résolution d’un bogue qui empêche la compilation quand un script est compilé avec un nom de fichier encodé au format web.

## <a name="2300"></a>2.3.0.0
 Publication : 14 juillet 2016

### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Général :**

    -   Ajout d’une option pour désactiver les journaux de console Unity dans la liste d’erreurs de Visual Studio.

    -   Ajout d’une option pour autoriser la modification des propriétés de projet générées.

-   **Débogueur :**

    -   Ajout des visualiseurs de chaînes de texte, XML, HTML et JSON.

-   **Assistants :**

    -   Ajout de MonoBehaviors manquants.

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Général :**

    -   Résolution d’un conflit lié à ReSharper, qui empêchait l’affichage des contrôles dans les paramètres de Visual Studio.

    -   Résolution d’un conflit lié à Xamarin, qui empêchait le débogage dans certaines situations.

-   **Débogueur :**

    -   Correction d’un problème provoquant le blocage de Visual Studio pendant le débogage.

    -   Correction d’un problème lié aux points d’arrêt de fonction dans Visual Studio 2015.

    -   Correction de plusieurs problèmes d’évaluation d’expression.

## <a name="2200"></a>2.2.0.0
 Publication : 4 février 2016

### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Assistants :**

    -   Ajout de la recherche intelligente dans l’Assistant **Implémenter MonoBehavior** .

    -   Prise en charge de l’affichage contextuel dans les Assistants (par exemple, les messages NetworkBehavior s’affichent uniquement si vous utilisez NetworkBehavior).

    -   Prise en charge supplémentaire de messages NetworkBehavior dans les Assistants.

-   **Interface utilisateur :**

    -   Ajout d’une option pour configurer la visibilité des messages MonoBehavior.

    -   Suppression des pages de propriétés de Visual Studio qui ne sont pas pertinentes pour les projets Unity.

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Génération de projet :**

    -   Correction des références à UnityEngine et UnityEditor sur Unity 4.6.

    -   Correction de la génération des fichiers projet quand Unity s’exécute sur OSX.

    -   Correction de la gestion des noms de projet contenant des caractères #.

    -   Limitation des projets générés à C# 4.

-   **Débogueur :**

    -   Correction d’un problème d’évaluation d’expression lors du débogage au sein d’une coroutine Unity.

    -   Correction d’un problème provoquant le blocage de Visual Studio pendant le débogage.

-   **Interface utilisateur :**

    -   Correction d’une incompatibilité avec l’extension [Tabs Studio](https://tabsstudio.com/) de Visual Studio.

-   **Programme d’installation :**

    -   Prise en charge de l’installation de VSTU au niveau de la machine (installation pour tous les utilisateurs) en créant des entrées de Registre HKLM.

    -   Correction des problèmes de désinstallation de VSTU quand la même version de VSTU est installée pour plusieurs versions différentes de Visual Studio. C’est le cas, par exemple, quand VSTU **2015** 2.1.0.0 et VSTU **2013** 2.1.0.0 ont été installés ensemble.

## <a name="2100"></a>2.1.0.0
 Publication : 8 septembre 2015

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Prise en charge d’Unity 5.2

### <a name="bug-fixes"></a>Correctifs de bogues

-   Afficher les éléments de menu sur Unity < 4.2

-   Un message d’erreur n’est plus affiché quand Visual Studio verrouille les fichiers XML intellisense.

-   Gérer les points d’arrêt conditionnels <\<When Changed>> quand l’argument conditionnel n’est pas une valeur booléenne.

-   Correction des références aux assemblys UnityEngine et UnityEditor pour les applications du Windows Store.

-   Correction de l’erreur lors de l’exécution pas à pas dans le débogueur : Impossible de parcourir, exception générale.

-   Correction du nombre d’accès des points d’arrêt dans Visual Studio 2015.

## <a name="2000"></a>2.0.0.0
 Publication : 20 juillet 2015

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Intégration Unity :**

    -   Correction de la conversion de symboles de débogage créés avec Visual Studio 2015 lors de l’importation d’une DLL et de ses symboles de débogage (PDB).

    -   Toujours générer des fichiers MDB lors de l’importation d’une DLL et de ses symboles de débogage (PDB), sauf quand un fichier MDB est également fourni.

    -   Correction de la pollution du répertoire du projet Unity avec un répertoire obj.

    -   Correction de la génération des références à System.Xml.Link et System.Runtime.Serialization.

    -   Ajout de la prise en charge de plusieurs abonnés aux raccordements API pour la génération du fichier projet.

    -   Toujours terminer la génération du fichier projet même quand l’un des fichiers à générer est verrouillé.

    -   Ajout de la prise en charge des caractères génériques (*) dans le filtre d’extension lors de la spécification des fichiers à inclure dans le projet C#.

-   **Intégration Visual Studio :**

    -   Correction d’un problème de compatibilité avec Productivity Power Tools.

    -   Correction de la génération de MonoBehaviors autour des déclarations d’événements et de délégués.

-   **Débogueur :**

    -   Correction d’un blocage potentiel lors du débogage.

    -   Correction d’un problème où les variables locales ne s’affichent pas dans certains frames de pile.

    -   Correction de l’inspection des tableaux vides.

## <a name="1990---20-preview-2"></a>1.9.9.0 - 2.0 préversion 2
 Publication : 2 avril 2015

### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Explorateur de projets Unity :**

    -   Renommer automatiquement la classe lorsque vous renommez un fichier dans l’Explorateur de projets Unity (voir la boîte de dialogue **Options** ).

    -   Sélectionner automatiquement les scripts nouvellement créés dans l’Explorateur de projets Unity.

    -   Suivre le script actif dans l’Explorateur de projets Unity (voir la boîte de dialogue **Options** ).

    -   Procéder à une synchronisation double de l’Explorateur de solutions Visual Studio (voir la boîte de dialogue **Options** ).

    -   Adopter les icônes de Visual Studio dans le projet Unity.

-   **Débogueur :**

    -   Sélectionner la cible de débogage active à partir d’une liste de cibles de débogage enregistrées ou récemment utilisées (voir la boîte de dialogue **Options** ).

    -   Créer des points d’arrêt sur fonction sur les méthodes MonoBehavior et appliquez-les à plusieurs classes MonoBehavior.

    -   Prendre en charge Générer l’ID de l’objet dans le débogueur.

    -   Prendre en charge le nombre d’accès à un point d’arrêt dans le débogueur.

    -   Prendre en charge l’exception sur point d’arrêt dans le débogueur (à titre expérimental. voir la boîte de dialogue **Options** ).

    -   Prendre en charge la création d’objets et de tableaux lors de l’évaluation d’expressions dans le débogueur.

    -   Prendre en charge la comparaison de valeurs null lors des expressions d’évaluation dans le débogueur.

    -   Filtrer les membres obsolètes dans les fenêtres Espion du débogueur.

-   **Programme d’installation :**

    -   Inscription optimisée de l’extension Visual Studio Tools pour Unity.

    -   Installer le package Visual Studio Tools pour Unity pour Unity 5.

-   **Documentation :** Améliorer les performances de la génération de la documentation.

-   **Assistants :** Prise en charge de nouvelles méthodes MonoBehavior pour Unity 4.6 et Unity 5.

-   **Unity :** Indicateurs de recherche non sécurisés et définitions personnalisées dans les fichiers .rsp pendant la génération du fichier projet.

-   **Interface utilisateur :** Ajout de la boîte de dialogue **Options** des Outils Visual Studio pour Unity dans Visual Studio.

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Explorateur de projets Unity :**

    -   Actualiser l’Explorateur de projets Unity après que les fichiers sont déplacés ou renommés à partir de l’Explorateur de solutions Visual Studio.

    -   Conserver les sélections lorsque vous renommez des fichiers dans l’Explorateur de projets Unity.

    -   Empêcher le développement / la réduction automatique lorsque l’utilisateur double-clique sur les fichiers dans l’Explorateur de projets Unity.

    -   S’assurer que les fichiers nouvellement sélectionnés sont visibles dans l’Explorateur de projets Unity.

-   **Débogueur :**

    -   Éviter un éventuel blocage de Visual Studio lors de l’évaluation des expressions dans le débogueur.

    -   S’assurer que les appels de méthode s’exécutent sur le domaine approprié dans le débogueur.

-   **Unity :**

    -   Corriger l’emplacement d’UnityVS.OpenFile avec Unity 5.

    -   Corriger l’emplacement de pdb2mdb avec Unity 5.

    -   Empêcher une possible exception pendant la génération du fichier projet.

    -   Éviter un blocage possible lors de l’exécution d’Unity sur OSX.

    -   Gérer les exceptions internes.

    -   Envoyer les journaux de console Unity à la liste d’erreurs Visual Studio.

-   **Documentation :** Corriger la génération de la documentation pour la nouvelle documentation Unity.

-   **Projet :** Déplacer et renommer les fichiers .meta Unity si nécessaire, même dans les dossiers.

-   **Assistants :** Corriger l’ordre des paramètres de la méthode MonoBehavior lors de la génération de code.

-   **Interface utilisateur :** Prendre en charge les thèmes Visual Studio pour les icônes et le menu contextuel.

## <a name="1980---20-preview"></a>1.9.8.0 - 2.0 préversion
 Publication : 12 novembre 2014

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Prise en charge de Visual Studio 2015.

-   Coloration du code pour les nuanceurs Unity dans Visual Studio 2015.

-   Visualisation améliorée des valeurs lors du débogage.

    -   Meilleure visualisation des ArrayLists, des listes, des tables de hachage et des dictionnaires.

    -   Afficher les membres non publics et les membres statiques en tant que catégories dans les vues espion et les vues locales.

    -   Affichage amélioré de SerializedProperty d’Unity pour évaluer uniquement le champ de valeur valide pour la propriété.

    -   Prise en charge de DebuggerDisplayAttribute pour les classes et les structs.

    -   Prise en charge de DebuggerTypeProxyAttribute support.

-   Effectuer l’insertion des méthodes MonoBehaviour à l’aide de nos assistants afin de respecter les conventions de codage des utilisateurs.

-   Implémenter la prise en charge des modèles de texte au moment de la compilation dans les projets UnityVS générés.

-   Implémenter la prise en charge des ressources ResX dans les projets UnityVS générés.

-   Prendre en charge l’ouverture des nuanceurs dans Visual Studio à partir d’Unity.

### <a name="bug-fixes"></a>Correctifs de bogues

-   Nettoyage des sockets avant le démarrage du jeu dans Unity après le déclenchement de l’attachement et de la lecture dans Visual Studio. Cela résout certains problèmes de stabilité de la connexion entre Unity et VS lors de l’utilisation de l’attachement et de la lecture.

-   Éviter l’appeler de méthodes dans l’interface du débogueur du moteur de script Unity qui sont enclines à figer Unity. Cela résout le blocage d’Unity lors de l’attachement du débogueur.

-   Résolution de l’affichage des piles d’appel quand aucun symbole n’est disponible.

-   Ne pas enregistrer le rappel du journal si ce n’est pas nécessaire.

## <a name="1920"></a>1.9.2.0
 Publication : 9 octobre 2014

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Améliorer la détection des joueurs Unity.

-   Lorsque vous utilisez notre ouvreur de fichiers, faites passer à Unity le numéro de ligne, ainsi que le nom du fichier.

-   Documentation Unity en ligne par défaut s’il n’existe aucune documentation locale.

### <a name="bug-fixes"></a>Correctifs de bogues

-   Corriger les incidents Unity potentiels lors de l’atteinte d’un point d’arrêt après rechargement d’un domaine.

-   Résoudre les exceptions affichées dans la console Unity lors de la fermeture de nos fenêtres Configuration ou About, après rechargement d’un domaine.

-   Corriger la détection des versions Unity 64 bits exécutées localement.

-   Corriger le filtrage des MonoBehaviours par version Unity dans les Assistants.

-   Fix bug where all assets were included in the project files if the extension filter was empty.

## <a name="1910"></a>1.9.1.0
 Publication : 22 septembre 2014

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Optimiser le point d’arrêt de la liaison vers les emplacements source.

-   Prise en charge des méthodes surchargées dans l’évaluation d’expression du débogueur.

-   Prise en charge des primitives de boxing et des types de valeur dans l’évaluation d’expression du débogueur.

-   Prise en charge de la recréation de l’environnement de variables locales C# lors du débogage des méthodes anonymes.

-   Supprimer et renommer les fichiers .meta lors de la suppression ou du changement de nom des fichiers à partir de Visual Studio.

### <a name="bug-fixes"></a>Correctifs de bogues

-   Corriger la gestion des thèmes Visual Studio. Avant, les boîtes de dialogue de thèmes noirs pouvaient apparaître vides.

-   Correction du problème de blocage d’Unity lors de la connexion du débogueur pendant la recompilation par Unity.

-   Corriger les points d’arrêt lors du débogage à distance des éditeurs ou des lecteurs compilés sur un autre système.

-   Résoudre un éventuel incident Visual Studio lorsqu’un point d’arrêt est atteint.

-   Corriger la liaison des points d’arrêt afin d’éviter que les points d’arrêt ne s’affichent comme déchargés.

-   Corriger la gestion de la portée des variables dans le débogueur pour éviter que des variables en direct n’apparaissent hors de portée.

-   Correction du problème de la recherche de membres statiques dans l’évaluation d’expression du débogueur.

-   Corriger l’affichage des types dans l’évaluation d’expression du débogueur pour afficher les propriétés et les champs statiques.

-   Corriger la génération de solution lorsque les noms de projet Unity incluent des caractères spéciaux que Visual Studio interdit (problème de connexion #948666).

-   Corriger le package Visual Studio Tools Unity pour arrêter immédiatement l’envoi d’événements à la console après que l’option a été désactivée (problème de connexion #933357).

-   Corriger la détection de références pour régénérer correctement les références aux nouvelles API comme UnityEngine.UI dans les projets générés par UnityVS.

-   Corriger le programme d’installation pour exiger que Visual Studio se ferme avant l’installation afin d’éviter des installations corrompues.

-   Corriger le programme d’installation pour installer les assemblys de référence Unity comme composants autonomes, partagés entre toutes les versions de VSTU.

-   Corriger l’ouverture de scripts avec VSTU dans les versions 64 bits d’Unity.

## <a name="1900"></a>1.9.0.0
 Publication : 29 juillet 2014

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Dans la fenêtre Attacher le débogueur Unity, ajoutez la possibilité d’entrer un port et une adresse IP personnalisés pour le débogage.

-   Ajouter l’option de configuration pour définir que Unity s’exécute en arrière-plan ou non.

-   Ajouter l’option de configuration pour générer les fichiers solution et projet ou uniquement les fichiers projet.

-   Cible de démarrage : choisir Attacher à Unity ou Attacher à Unity et lire.

-   Affichage de tableaux multidimensionnels dans le débogueur.

-   Gérer les nouveaux ports de débogage du lecteur Unity.

-   Gérer les références aux nouveaux assemblys Unity comme les assemblys GUI 4.6 d’Unity.

-   Déconstruit les fermetures pour afficher correctement les variables locales lors du débogage.

-   Déconstruit les variables générées des itérateurs en arguments lors du débogage.

-   Conserver l’état de l’Explorateur de projet Unity après rechargement d’un projet.

-   Ajouter une commande pour synchroniser l’Explorateur de projets Unity avec le document en cours.

### <a name="bug-fixes"></a>Correctifs de bogues

-   Corriger les points d’arrêt conditionnels dont les conditions sont définies avant le démarrage du débogueur.

-   Résoudre les références à UnityEngine afin d’éviter des avertissements.

-   Résolution de l’analyse des versions pour les versions Unity bêta.

-   Corriger le problème où les variables n’apparaissent pas dans la fenêtre de variables locales lors de l’atteinte d’un point d’arrêt ou du parcours pas à pas.

-   Corriger les info-bulles des variables dans Visual Studio 2013.

-   Corriger la génération de la documentation IntelliSense pour Unity 4.5.

-   Corriger la communication Unity / Visual Studio après le rechargement d’un domaine (lire/arrêter dans Unity).

-   Corriger la gestion des composants dans les thèmes Visual Studio.

> [!IMPORTANT]
>  C# étant le langage prédominant de l’écosystème Unity - les nouvelles ressources d’exemples sont en C#, la documentation Unity sera par défaut en C# -, nous avons supprimé notre support de base pour UnityScript et pour Boo afin de mieux se concentrer sur l’expérience C#. Par conséquent, les solutions VSTU sont désormais en C# uniquement et beaucoup plus rapides à charger.

## <a name="1820"></a>1.8.2.0
 Publication : 7 janvier 2014

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Contourner un problème dans la couche réseau du moteur de script de Unity sur Mavericks pour la découverte à distance d’éditeurs.

-   Gérer les nouveaux ports pour découvrir les lecteurs Unity à distance.

-   Référencer l’assembly UnityEngine spécifique à la cible de génération en cours.

-   Ajouter le paramètre pour filtrer les fichiers à inclure dans les projets générés.

-   Ajouter le paramètre pour désactiver l’envoi de journaux de console à la liste d’erreurs Visual Studio. Cela est utile si vous utilisez PlayMaker ou Console Pro, car il peut n’y avoir qu’un seul rappel enregistré dans Unity pour recevoir des journaux de la console.

-   Ajouter le paramètre pour désactiver la génération des symboles de débogage mdb. Cette option est utile si vous générez la mdb vous-même.

### <a name="bug-fixes"></a>Correctifs de bogues

-   Corriger une régression lorsque les fichiers ouverts dans Visual Studio à partir de Unity > = 4.2 perdraient IntelliSense.

-   Corriger les boîtes de dialogue Visual Studio pour gérer les thèmes personnalisés.

-   Corriger la fermeture du menu contextuel de l’UPE.

-   Empêcher un incident dans Unity lorsque l’assembly généré spécifique à la version est désynchronisé.

## <a name="1810"></a>1.8.1.0
 Publication : 21 novembre 2013

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Ajustement des Assistants MonoBehaviour avec les API Unity 4.3.

-   Les Assistants MonoBehaviour filtrent les API Unity selon la version que vous utilisez.

-   Ajouter une référence à System.Xml.Linq aux projets de Unity > 4.1.

-   Agrémenter les appels à Debug.Log pour ne pas inclure le début du Stack Trace dans le message.

### <a name="bug-fixes"></a>Correctifs de bogues

-   Correction d’un bogue dans lequel nous interférons avec la gestion par défaut des fichiers JavaScript dans Visual Studio.

-   Correction du pixel blanc apparaissant dans Visual Studio, en vrai cette fois.

-   Correction de la suppression de l’assembly UnityVS.VersionSpecific s’il est marquée en lecture seule par un SCM.

-   Fixed exceptions when creating sockets in the UnityVS package.

-   Correction d’un incident dans Visual Studio lors du chargement d’images en stock à partir d’assemblys Visual Studio.

-   Correction d’un bogue dans la génération d’UnityVS.VersionSpecific pour les générations de code source d’Unity.

-   Correction d’un blocage possible lors de l’ouverture d’un socket dans le package Unity.

-   Correction de la gestion du projet Unity avec un tiret (-) dans le nom.

-   Correction des scripts d’ouverture d’Unity à ne pas confondre pas la commande ALT+TAB pour Unity 4.2 et versions ultérieures.

## <a name="1800"></a>1.8.0.0
 Publication : 24 septembre 2013

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Amélioration spectaculaire de la vitesse de connexion du débogueur.

-   Gestion automatique de la navigation vers un fichier et une ligne dans Unity 4.2 et versions ultérieures.

-   Points d’arrêt conditionnels.

-   Le générateur de fichiers de projet gère désormais les modèles T4.

-   Mettre à jour les Assistants MonBehavior avec les nouvelles API.

-   Documentation d’IntelliSense dans C# pour les types Unity.

-   Évaluation des expressions arithmétiques et logiques.

-   Meilleure découverte des éditeurs distants pour l’aperçu de débogage distant.

### <a name="bug-fixes"></a>Correctifs de bogues

-   Correction d’un bogue avec fuite d’un thread dans Visual Studio après déconnexion du débogueur.

-   Correction d’un pixel blanc apparaissant dans Visual Studio.

-   Correction de la gestion des clics sur l’icône de barre d’état.

-   Correction de la génération des références avec les assemblys des dossiers Plugins.

-   Correction de la création de sockets à partir du package UnityVS en cas d’exceptions.

-   Correction de la détection de nouvelles versions d’UnityVS.

-   Correction de l’invite du Gestionnaire de licences lors de l’expiration de la licence.

-   Correction d’un bogue qui peut afficher vide la liste des processus dans la fenêtre de l’attachement du débogueur au processus de Visual Studio.

-   Correction de la modification des valeurs booléennes dans la vue locale.

## <a name="1220"></a>1.2.2.0
 Publication : 9 juillet 2013

### <a name="bug-fixes"></a>Correctifs de bogues

-   Gérer les noms complets dans l’évaluateur d’expression.

-   Correction d’un blocage lié à la gestion des exceptions où le moteur de script Unity envoie des données incorrectes de StackFrame.

-   Correction du processus de génération pour les cibles du Web.

-   Correction d’une erreur susceptible de se produire si Visual Studio a été démarré et qu’un fichier supprimé se trouvait dans la liste des fichiers à ouvrir au démarrage.

-   Correction d’UnityVS.OpenFile pour gérer les fichiers autres que les fichiers script, comme les nuanceurs compilés.

-   Il est maintenant fait référence à Boo.Lang et UnityScript.Lang à partir de tous les projets C#.

-   Correction de la génération des références dans les projets si le projet comporte des caractères spéciaux.

-   Contournement d’un problème VS où les appels de méthode à des projets supprimés déclenchent plusieurs zones de message NullReferenceException.

-   Correction de la gestion des assemblys de la version bêta Unity 4.2.

## <a name="1210"></a>1.2.1.0
 Publication : 9 avril 2013

### <a name="bug-fixes"></a>Correctifs de bogues

-   Correction du déploiement local des assemblys Unity pour l’exécution de code en cas d’erreur d’E/S (telle que fichiers en lecture seule ou fichiers verrouillés par Visual Studio).

-   Correction d’une régression où de l’ouverture d’un script à partir d’Unity ne traiterait pas le fichier s’il était déjà ouvert dans Visual Studio.

-   Correction de problème de performances de la nouvelle gestion des exceptions.

-   Correction de la liaison des points d’arrêt dans certaines DLL externes.

## <a name="1200"></a>1.2.0.0
 Publication : 25 mars 2013

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Amélioration spectaculaire de la vitesse de connexion du débogueur.

-   Explorateur de projets Unity optimisé pour les grands projets.

-   Respecte les paramètres de Visual Studio pour interrompre (ou pas) géré et les exceptions non gérées.

-   Respecte le paramètre de Visual Studio pour l’appel de ToString sur les variables locales.

-   Ajouter un nouveau menu Débogage -> Attacher le débogueur Unity, que vous pouvez utiliser pour déboguer les lecteurs Unity.

-   Conserver les projets personnalisés ajoutés à la solution UnityVS lors de la génération du fichier solution.

-   Ajouter nouveau raccourci clavier CTRL+ ALT M -> CTRL+H pour afficher la documentation Unity pour la fonction Unity ou un membre à la position du point d’insertion.

-   Prendre les fichiers de réponse du compilateur (rsp) en compte lors de la compilation à partir de Visual Studio.

-   Décomposer les types générés par le compilateur pour afficher les variables lorsque vous déboguez des méthodes de générateur.

-   Simplifier le débogage à distance en supprimant la nécessité de configurer un dossier partagé sur Unity. Maintenant, vous devez simplement avoir accès à votre projet Unity à partir de Windows.

-   Installer un profil Unity personnalisé comme profil cible .net standard. Corrige tous les faux positifs que ReSharper peut afficher.

-   Contourner un bogue du moteur de script Unity, afin que le débogueur ne s’arrête pas sur les threads non correctement inscrits.

-   Correction de l’ouverture de fichier pour éviter une condition de concurrence dans Visual Studio où il est dit qu’il est possible d’ouvrir les fichiers et qu’un incident se produit à la demande d’ouverture.

-   UnityVS demande maintenant d’actualiser la build lorsque Visual Studio génère le projet, et non plus lors de l’enregistrement du fichier.

### <a name="bug-fixes"></a>Correctifs de bogues

-   Correction de notre profil .net personnalisé

-   Correction de l’intégration de thèmes, qui résout les problèmes avec le thème foncé Visual Studio 2012.

-   Correction du raccourci de comportement rapide dans Visual Studio 2012.

-   Correction d’un problème de pas à pas qui peut se produire lors du débogage et qu’un thread non principal atteint un point d’arrêt.

-   Correction de l’achèvement UnityScript et Boo des alias de type, tel qu’int.

-   Correction d’exception lors de l’écriture d’une nouvelle chaîne UnityScript ou Boo.

-   Correction des exceptions dans les menus Unity lorsqu’une solution n’a pas été chargée.

-   Correctif de bogue UVS-48 : la saisie de guillemets doubles produit parfois des erreurs et arrête toutes les fonctions (exécution de code, mise en surbrillance de la syntaxe, etc.).

-   Résolution de bogue UVS-46 : Duplication du fichier de script ouvert (UnityScript) quand vous cliquez sur la liste d’erreurs de Visual Studio.

-   Résolution de bogue UVS-42 : Le logo de connectivité Unity dans la barre d’état ne traite pas les événements de souris dans Visual Studio 2012.

-   Résolution de bogue UVS-44 : La combinaison Ctrl+Maj+Q n’est pas disponible dans Visual Studio 2012 pour les MonoBehaviours rapides.

-   Résolution de bogue UVS-40 : Les éléments sélectionnés dans l’Explorateur de projets Unity sont illisibles quand la fenêtre est inactive dans le thème « foncé » de Visual Studio 2012.

-   Résolution de bogue UVS-39 : Problème de création de jetons pour les chaînes d’échappement.

-   Résolution de bogue UVS-35 : Appel de ToString sur des objets durant l’inspection de variables.

-   Résolution de bogue UVS-27 : Incohérence de la fenêtre Aller au symbole avec le thème « foncé » dans Visual Studio 2012.

-   Résolution de bogue UVS-11 : Variables locales dans les coroutines.

## <a name="1100---beta-release"></a>1.1.0.0 - Version bêta
 Publication : 9 mars 2013

## <a name="10130"></a>1.0.13.0
 Publication : 21 janvier 2013

### <a name="bug-fixes"></a>Correctifs de bogues

-   Correction d’un blocage de Visual Studio qui peut se produire si le programme débogué cible envoie des événements de thread non valides. Cela se produit généralement lors du débogage d’un Unity distant sur OSX.

-   Correction d’une recherche Visual Studio qui peut se produire si une exception arrête le débogueur.

-   Correction des programmes d’assistance MonoBehavior lorsqu’un MonoBehavior C# figure dans un espace de noms.

-   Correction des info-bulles du débogueur pour UnityScript dans Visual Studio 2012.

-   Correction de la génération de projet lorsque seules les constantes de débogage sont modifiés à partir d’Unity.

-   Correction de la navigation au clavier dans l’Explorateur de projets Unity.

-   Correction de la colorisation UnityScript pour les chaînes d’échappement.

-   Correction de l’ouvreur de fichiers pour mieux deviner le nom du projet en cas d’utilisation en dehors d’Unity. Cela est nécessaire lorsque l’utilisateur utilise un ouvreur de fichiers tiers dans Unity qui délègue à UnityVS.

-   Correction de la gestion de longs messages envoyés d’Unity à UnityVS. Avant cela, les longs messages pouvaient bloquer la partie messagerie d’UnityVS. Par conséquent, il arrivait que UnityVS ne puisse pas ouvrir un fichier à partir d’Unity.

## <a name="10120"></a>1.0.12.0
 Publication : 3 janvier 2013

### <a name="bug-fixes"></a>Correctifs de bogues

-   Correction du verrouillage de Visual Studio qui peut se produire lorsque Visual Studio supprime un point d’arrêt.

-   Correction d’un bogue dans lequel certains points d’arrêt ne sont pas atteints après que Unity a recompilé les scripts de jeu.

-   Correction du débogueur pour informer correctement Visual Studio lorsque des points d’arrêt ont été séparés.

-   Correction d’un problème d’enregistrement susceptible d’empêcher le débogueur Visual Studio de déboguer les programmes natifs.

-   Correction d’une exception susceptible de se produire lors de l’évaluation d’expressions UnityScript et Boo.

-   Correction d’une régression dans laquelle la modification du niveau de l’API .NET dans Unity ne déclenche pas une mise à jour des fichiers projet.

-   Correction d’un problème d’API où le code utilisateur ne peut participer au Gestionnaire de rappel du journal.

## <a name="10110"></a>1.0.11.0
 Publication : 28 novembre 2012

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Prise en charge officielle de Unity 4.

-   Manipulation des scripts à partir de l’Explorateur de projets Unity.

-   Intégration dans la fenêtre Naviguer vers de Visual Studio.

-   Analyse du message de la console Info, afin qu’un clic sur la liste d’erreurs vous permette d’accéder à la première StackFrame avec symboles.

-   Ajouter une [API](../cross-platform/customize-project-files-created-by-vstu.md) pour permettre à utilisateur de participer à la génération du projet.

-   Ajouter une [API](../cross-platform/share-the-unity-log-callback-with-vstu.md) pour permettre à utilisateur de participer au rappel de journal.

### <a name="bug-fixes"></a>Correctifs de bogues

-   Correction de la régression dans l’arrière-plan de l’Explorateur de projets Unity dans Visual Studio 2012.

-   Correction de la génération de projet pour les utilisateurs du profil .net complet.

-   Correction de la génération de projet pour les utilisateurs de la cible Web.

-   Correction de la génération de projet pour inclure les symboles de compilation DEBUG et TRACE comme le fait Unity.

-   Correction d’incident lors de l’utilisation de caractères spéciaux dans la fenêtre Accéder au symbole.

-   Correction du problème s’il n’est pas possible d’injecter notre icône dans la barre d’état de Visual Studio.

## <a name="10100"></a>1.0.10.0
 Publication : 9 octobre 2012

### <a name="bug-fixes"></a>Correctifs de bogues

-   Correction de l’arrière-plan de l’Explorateur de projets Unity dans Visual Studio 2010.

-   Correction d’un blocage de Visual Studio qui peut se produire si UnityVS a tenté d’attacher le débogueur à instance Unity dont l’interface du débogueur s’est précédemment bloquée.

-   Résolution d’un blocage de Visual Studio qui peut se produire quand un point d’arrêt a été défini et qu’un rechargement d’AppDomain a lieu.

-   Résolution de la façon d’extraire des assemblys d’Unity pour éviter le verrouillage des fichiers et confondre le processus de génération d’Unity.

## <a name="1090"></a>1.0.9.0
 Publication : 3 octobre 2012

### <a name="bug-fixes"></a>Correctifs de bogues

-   Résolution de la génération de projet lorsque le projet Unity inclut les ressources JavaScript réelles.

-   Résolution de la gestion des erreurs dans l’évaluation d’expression.

-   Résolution de la définition de nouvelles valeurs en champs de types valeur.

-   Résolution des effets secondaires éventuels lorsque vous pointez sur des expressions à partir de l’éditeur de code.

-   Résolution de la façon dont les types sont recherchés dans les assemblys chargés pour l’évaluation d’expression.

-   Résolution de bogue UVS-21 : L’évaluation de l’affectation sur les objets Unity n’a aucun effet.

-   Résolution de bogue UVS-21 : Pointeur non valide durant l’évaluation d’un appel de méthode à l’API Math Unity.

## <a name="1080"></a>1.0.8.0
 Publication : 26 septembre 2012

### <a name="bug-fixes"></a>Correctifs de bogues

-   Résolution de la façon dont notre ouvreur de script a acquis le chemin d’accès au projet pour s’assurer qu’il peut ouvrir Visual Studio et les scripts.

-   Résolution d’un bogue avec les points d’arrêt créés pendant que la session de débogage était en cours d’exécution et entraînait le verrouillage de Visual Studio.

-   Résolution de la façon dont UnityVS est enregistré sur Visual Studio 2010.

## <a name="1070"></a>1.0.7.0
 Publication : 14 septembre 2012

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Prise en charge de Visual Studio 2012.

### <a name="bug-fixes"></a>Correctifs de bogues

-   Résolution de la génération des fichiers de projet de plug-ins et d’éditeur pour correspondre au comportement d’Unity.

-   Résolution de la traduction de symboles .pdb sur Unity 4.

> [!IMPORTANT]
>  En raison de la prise en charge de Visual Studio 2012, nous avons dû renommer quelques fichiers et déplacer d’autres. Le package UnityVS pour importer Unity est maintenant appelé UnityVS 2010 ou UnityVS 2012, pour, respectivement, Visual Studio 2010 et Visual Studio 2012. Cette version requiert également que les fichiers de projet UnityVS soient régénérés.

## <a name="1060---internal-build"></a>1.0.6.0 - Build interne
 Publication : 12 septembre 2012

## <a name="1050"></a>1.0.5.0
 Publication : 10 septembre 2012

### <a name="bug-fixes"></a>Correctifs de bogues

-   Résolution de la génération des fichiers projet lorsque les scripts ou les nuanceurs ont un caractère xml non valide.

-   Résolution de la détection d’instances Unity quand Unity a été connecté au serveur de ressources. Cela s’est traduit par un échec à l’ouverture de fichiers à partir de Unity et de la connexion automatique du débogueur Visual Studio.

## <a name="1040"></a>1.0.4.0
 Publication : 5 septembre 2012

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Conversion automatique des symboles de débogage dans Unity.

     Si vous avez un assembly .dll .NET avec son .pdb associé dans votre dossier Composants, réimportez simplement l’assembly et UnityVS convertira le fichier .pdb en un fichier de symboles de débogage que le moteur de script d’Unity comprend, et vous pourrez effectuer un pas à pas détaillé dans vos assemblys .NET à partir de UnityVS.

### <a name="bug-fixes"></a>Correctifs de bogues

-   Résolution de l’incident UnityVS lors du débogage provoqué par les exceptions levées par des méthodes ou propriétés à l’intérieur d’Unity.

## <a name="1030"></a>1.0.3.0
 Publication : 4 septembre 2012

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Nouvelle option de configuration pour désactiver l’utilisation d’UnityVS pour ouvrir des fichiers à partir d’Unity.

### <a name="bug-fixes"></a>Correctifs de bogues

-   Résolution de la génération des références à UnityEditor pour les projets autres que les projets éditeur.

-   Résolution de la définition du symbole UNITY_EDITOR pour les projets non éditeur.

-   Résolution des pannes VS aléatoires causés par notre barre d’état personnalisé.

## <a name="1020"></a>1.0.2.0
 Publication : 30 août 2012

### <a name="bug-fixes"></a>Correctifs de bogues

-   Résolution du Conflit avec le débogueur PythonTools.

-   Résolution des références à Mono.Cecil.

-   Résolution du bogue dans la façon dont les scripts des assemblys ont été extraits d’Unity avec Unity 4 b7.

## <a name="1010"></a>1.0.1.0
 Publication : 28 août 2012

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Prise en charge de l’aperçu pour la version Unity 4.0 bêta.

### <a name="bug-fixes"></a>Correctifs de bogues

-   Résolution de l’inspection des propriétés levant des exceptions.

-   Résolution de la descente dans les objets de base lors de l’inspection des objets.

-   Résolution de liste déroulante vide pour le point d’insertion dans l’Assistant MonoBehavior.

-   Résolution de l’exécution de la DLL dans le dossier Ressources pour UnityScript et Boo.

## <a name="1000---initial-release"></a>1.0.0.0 - Version initiale
 Publication : 22 août 2012
