---
title: 'Zone d’essai 6 : Supprimer Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9902ab9d1cb9c28ddf67b83590a4cccd5f6562f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704510"
---
# <a name="test-area-6-delete"></a>Zone de test 6 : Supprimer
Cette zone de test plug-in de contrôle des sources couvre les actions de suppression.

 Le contrôle des sources répond à la suppression des actions dans **Solution Explorer**.

 Voici une liste d’éléments qui peuvent être supprimés :

- Fichiers

- Dossiers

- Projet

  Selon le type de projet, vous pourriez avoir la possibilité de **supprimer** le projet (laisse les fichiers sur disque) ou **supprimer** le projet (supprime les fichiers sur le disque). L’action supprime le projet ou l’élément de **Solution Explorer**.

## <a name="expected-behavior"></a>Comportement attendu
 Le comportement attendu pour les cas de test dans la zone de test de suppression est :

- L’élément supprimé n’est plus visible dans **Solution Explorer**.

- Le parent du projet ou de l’élément supprimé est vérifié au besoin (éventuellement avec une invite.)

- Après avoir supprimé un article vérifié ou ajouté, il n’apparaît PAS dans la fenêtre **Checkins en attente.**

- L’article existe toujours dans le magasin de contrôle source, même après la suppression, et doit être purgé manuellement.

|Action|Étapes d’essai|Résultats attendus pour vérifier|
|------------|----------------|--------------------------------|
|Supprimer un projet client|1. Créer un projet client.<br />2. Ajouter la solution au contrôle des sources.<br />3. Supprimer l’ensemble du projet de la solution|Comportement attendu commun.|
|Supprimer un fichier vide|1. Créer un projet client.<br />2. Ajouter un fichier d’ente zéro au projet.<br />3. Ajouter la solution au contrôle des sources.<br />4. Sélectionnez le fichier, supprimez-le.|Comportement attendu commun.|
|Supprimer un dossier avec un fichier|1. Créer une solution de projet unique.<br />2. Ajouter un dossier.<br />3. Ajouter un fichier au dossier.<br />4. Ajouter la solution au contrôle des sources.<br />5. Consultez le projet pour éviter les invites.<br />6. Supprimer le dossier.|Comportement attendu commun.|
|Supprimer un projet Web du système de fichiers|1. Créer un projet Web de système de fichiers (utiliser le bouton Parcourir pour spécifier un chemin UNC).<br />2. Ajouter la solution au contrôle des sources.<br />3. Retirez l’ensemble du projet de la solution.<br />4. Répéter les étapes 1 à 3 pour un projet Web local (exerce des voies différentes à travers le code, mais a la même interface externe et le même comportement).|Comportement attendu commun.|
|Supprimer un fichier d’un projet Web du système de fichiers|1. Créer un projet Web de système de fichiers.<br />2. Ajouter la solution au contrôle des sources.<br />3. Supprimer un fichier du projet.<br />4. Répéter les étapes 1 à 3 pour un projet Web local (exerce des voies différentes à travers le code, mais a la même interface externe et le même comportement).|Comportement attendu commun.|

## <a name="see-also"></a>Voir aussi
- [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
