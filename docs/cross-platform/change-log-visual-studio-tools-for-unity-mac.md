---
title: Journal des modifications (Visual Studio Tools pour Unity, Mac) | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 197701258a47b3edc49f4e9477c6634d17b22920
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43775185"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Journal des modifications (Outils Visual Studio pour Unity, Mac)
Journal des modifications Visual Studio Tools pour Unity

## <a name="1602"></a>1.6.0.2
 Publiée le 24 juillet 2018

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Intégration :**

     -   Restauration de la solution de contournement d’un bogue de performances Unity corrigé par Unity.
     
## <a name="1601"></a>1.6.0.1
 Publiée le 10 juillet 2018

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Intégration :**

     -   Résolution du problème de pris en charge de la coloration de code du nuanceur.
     
## <a name="1600"></a>1.6.0.0
 Publiée le 26 juin 2018

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Assistants :**

    -   Faute de frappe corrigée pour le message de OnApplicationFocus.

-   **Génération de projet :**

     -   Solution de contournement temporaire pour un bogue de performances Unity : mise en cache de MonoIslands lors de la génération des projets.
     
     -   Ne convertissez plus un fichier pdb portable en mdb lors de l’utilisation du nouveau runtime Unity.
     
## <a name="1502"></a>1.5.0.2
 Publiée le 18 avril 2018
 
### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Intégration :**

    -   Ajout de la prise en charge de la complétion de code du nuanceur de base.
    
    -   Ajout de la prise en charge de l’activation/désactivation des commentaires dans les fichiers du nuanceur.

## <a name="1501"></a>1.5.0.1
 Publiée le 28 mars 2018
 
### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Intégration :**

    -   Ajout de la prise en charge de modèles supplémentaires dans l’Explorateur de projets Unity.

## <a name="1500"></a>1.5.0.0
 Publiée le 21 mars 2018
 
### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Intégration :**

    -   Ajout de la prise en charge de la détection et de l’attachement pour les lecteurs Android connectés via USB.

## <a name="1403"></a>1.4.0.3
 Publiée le 5 mars 2018
 
### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Génération de projet :**

    -   Ajout de la prise en charge du nouveau générateur de projet dans Unity 2018.1.

-   **Intégration :**

    -   Ajout d’un panneau d’options pour les paramètres dédiés.

## <a name="1402"></a>1.4.0.2
 Publiée le 24 janvier 2018
 
### <a name="bug-fixes"></a>Correctifs de bogues

-   **Génération de projet :**

    -   Détection de la version mono fixe.

-   **Intégration :**

    -   Résolution des problèmes de synchronisation avec 2018.1 et activation du plug-in.

    -   Correction des notifications lors de la détection d’un nouveau lecteur.

## <a name="1401"></a>1.4.0.1
 Publiée le 23 janvier 2018
 
### <a name="bug-fixes"></a>Correctifs de bogues

-   **Intégration :**

    -   Correction du développement/réduction des dossiers lors d’un double-clic

## <a name="1400"></a>1.4.0.0
 Publiée le 13 décembre 2017
 
### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Génération de projet :**

    -   Ajout de la prise en charge de .NET Standard.

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Intégration :**

    -   Correction du problème de conversion automatique des symboles de débogage pdb-mdb.

## <a name="1301"></a>1.3.0.1
 Publiée le 12 décembre 2017
 
### <a name="bug-fixes"></a>Correctifs de bogues

-   **Intégration :**

    -   Correction de l’appel indirect à EditorPrefs.GetBool affectant l’inspecteur lors de la tentative de modifier la taille du tableau.

-   **Assistants :**

    -   Actualiser le contexte roslyn avant d’insérer la méthode.

## <a name="1300"></a>1.3.0.0
 Publiée le 20 novembre 2017
 
### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Assistants :**

    -   Ajout de l’Assistant « Implémentation de message Unity ».

    -   Ajout de la prise en charge de la nouvelle API de complétion dans Visual Studio pour Mac 7.4.

## <a name="1200"></a>1.2.0.0
 Publiée le 23 octobre 2017
 
### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Débogueur :**

    -   Ajout de la prise en charge des fichiers de symboles de débogage portables.

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Génération de projet :**

    -   Correction du problème de l’ajout d’une extension .dll supplémentaire au nom du fichier d’assembly.

    -   Ne forcez pas l’indicateur Unity AllowAttachedDebuggingOfEditor, car la valeur par défaut est maintenant true.

## <a name="1103"></a>1.1.0.3
 Publiée le 23 octobre 2017
 
### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Génération de projet :**

    -   Ajout de la prise en charge du profil .NET 4.6.

## <a name="1102"></a>1.1.0.2
 Publiée le 8 août 2017
 
### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Débogueur :**

    -   Démarrez la boîte de dialogue Attacher au processus si ne savez pas à quel Unity attacher.

-   **Génération de projet :**

    -   Activation de l’option du compilateur Autoriser le code unsafe quand Unity 5.6 est utilisé.

## <a name="1101"></a>1.1.0.1
 Publiée le 20 juillet 2017
 
### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Intégration :**

    -   Ajout de la prise en charge des ressources localisées.

## <a name="1100"></a>1.1.0.0
 Publiée le 12 juillet 2017
 
### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Intégration :**

    -   Ajout de la prise en charge de l’attachement à des lecteurs et des éditeurs via la fenêtre Attacher au processus.

-   **Génération de projet :**

    -   Correction des références de nom d’assembly avec des fichiers mcs.rsp.

    -   Ajout de la prise en charge des unités de compilation assembly.json.    

    -   Correction des définitions avec des niveaux d’API.    

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Intégration :**

    -   Correction du message d’erreur du nuanceur lors de la compilation.

## <a name="1001"></a>1.0.0.1
 Publiée le 4 mai 2017
 
### <a name="bug-fixes"></a>Correctifs de bogues

-   **Intégration :**

    -   Correction du suivi de document actif avec les projets hybrides et réguliers.

## <a name="1000"></a>1.0.0.0
 Publiée le 3 mai 2017
