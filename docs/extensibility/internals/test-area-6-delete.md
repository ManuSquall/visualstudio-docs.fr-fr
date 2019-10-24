---
title: 'Zone de test 6 : supprimer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d75721a09615026cd10a42e4b6d8d8520b41239
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722444"
---
# <a name="test-area-6-delete"></a>Zone de test 6 : Supprimer
Cette zone de test du plug-in de contrôle de code source couvre les actions de suppression.

 Le contrôle de code source répond aux actions de suppression dans **Explorateur de solutions**.

 Voici une liste des éléments qui peuvent être supprimés :

- Fichiers

- Contenus

- Projet

  Selon le type de projet, vous pouvez avoir la possibilité de **supprimer** le projet (en laissant les fichiers sur le disque) ou de **supprimer** le projet (supprime les fichiers sur le disque). L’une ou l’autre action supprime le projet ou l’élément de **Explorateur de solutions**.

## <a name="expected-behavior"></a>Comportement attendu
 Le comportement attendu pour les cas de test dans la zone de test de suppression est le suivant :

- L’élément supprimé n’est plus visible dans **Explorateur de solutions**.

- Le parent du projet ou de l’élément supprimé est extrait en fonction des besoins (éventuellement à l’aide d’une invite).

- Une fois que vous avez supprimé un élément extrait ou ajouté, il n’apparaît pas dans la fenêtre **archivages en attente** .

- L’élément existe toujours dans le magasin de contrôle de code source, même après la suppression, et doit être purgé manuellement.

|Action|Étapes de test|Résultats attendus à vérifier|
|------------|----------------|--------------------------------|
|Supprimer un projet client|1. Créez un projet client.<br />2. Ajoutez la solution au contrôle de code source.<br />3. supprimer l’intégralité du projet de la solution|Comportement attendu courant.|
|Supprimer un fichier vide|1. Créez un projet client.<br />2. Ajoutez un fichier de zéro octet au projet.<br />3. Ajoutez la solution au contrôle de code source.<br />4. Sélectionnez le fichier, supprimez-le.|Comportement attendu courant.|
|Supprimer un dossier avec un fichier|1. Créez une solution de projet unique.<br />2. Ajoutez un dossier.<br />3. Ajoutez un fichier au dossier.<br />4. Ajoutez la solution au contrôle de code source.<br />5. consultez le projet pour éviter les invites.<br />6. Supprimez le dossier.|Comportement attendu courant.|
|Supprimer un projet Web de système de fichiers|1. Créez un projet Web de système de fichiers (utilisez le bouton Parcourir pour spécifier un chemin d’accès UNC).<br />2. Ajoutez la solution au contrôle de code source.<br />3. Supprimez l’intégralité du projet de la solution.<br />4. Répétez les étapes 1 à 3 pour un projet Web local (teste différents chemins d’accès à travers le code, mais ayant la même interface et le même comportement externes).|Comportement attendu courant.|
|Supprimer un fichier d’un projet Web de système de fichiers|1. Créez un projet Web de système de fichiers.<br />2. Ajoutez la solution au contrôle de code source.<br />3. supprimer un fichier du projet.<br />4. Répétez les étapes 1 à 3 pour un projet Web local (teste différents chemins d’accès à travers le code, mais ayant la même interface et le même comportement externes).|Comportement attendu courant.|

## <a name="see-also"></a>Voir aussi
- [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)