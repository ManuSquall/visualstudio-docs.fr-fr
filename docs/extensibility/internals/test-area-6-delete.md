---
title: 'Zone de test 6 : Supprimer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3fff473dbd4e3bc70f1b6308ed0d6b1129c95e2c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53930103"
---
# <a name="test-area-6-delete"></a>Zone de test 6 : Supprimer
Cette zone de test plug-in de contrôle de code source couvre les actions de suppression.  
  
 Contrôle de code source répond pour supprimer des actions dans **l’Explorateur de solutions**.  
  
 Voici une liste d’éléments qui peuvent être supprimées :  
  
- Fichiers  
  
- Dossiers  
  
- Projet  
  
  Selon le type de projet peut avoir la possibilité **supprimer** le projet (laisse les fichiers sur le disque) ou **supprimer** le projet (supprime les fichiers sur disque). L’action supprime le projet ou l’élément à partir de **l’Explorateur de solutions**.  
  
## <a name="expected-behavior"></a>Comportement attendu  
 Le comportement attendu pour les cas de test dans la zone de test delete est :  
  
-   Élément supprimé n’est plus visible dans **l’Explorateur de solutions**.  
  
-   Le parent du projet supprimé ou de l’élément est extrait en fonction des besoins (et éventuellement avec une invite de commandes.)  
  
-   Une fois que vous supprimez un checked out ou élément ajouté, il n’apparaît pas dans le **archivages en attente** fenêtre.  
  
-   L’élément existe dans le magasin de contrôle source, même après la suppression, toujours et doit être purgée manuellement.  
  
|Action|Étapes de test|Résultats attendus pour vérifier|  
|------------|----------------|--------------------------------|  
|Supprimer un projet de client|1.  Créez un projet client.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Supprimer l’ensemble du projet de solution|Comportement attendu commun.|  
|Supprimer un fichier vide|1.  Créez un projet client.<br />2.  Ajouter un fichier de zéro octet au projet.<br />3.  Ajouter la solution au contrôle de code source.<br />4.  Sélectionnez le fichier, supprimez-le.|Comportement attendu commun.|  
|Supprimer un dossier avec un fichier|1.  Créer la solution de projet unique.<br />2.  Ajouter un dossier.<br />3.  Ajouter un fichier dans le dossier.<br />4.  Ajouter la solution au contrôle de code source.<br />5.  Extraire le projet pour éviter les invites.<br />6.  Supprimez le dossier.|Comportement attendu commun.|  
|Supprimer un projet Web de système de fichiers|1.  Créez un projet Web de système de fichiers (utilisez le bouton Parcourir pour spécifier un chemin d’accès UNC).<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Supprimer l’ensemble du projet à partir de la solution.<br />4.  Répétez les étapes 1 à 3 pour un projet Web local (différents chemins d’accès via le code mais a la même interface externe et le comportement).|Comportement attendu commun.|  
|Supprimer un fichier à partir d’un projet Web de système de fichiers|1.  Créer un projet Web de système de fichiers.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Supprimer un fichier à partir du projet.<br />4.  Répétez les étapes 1 à 3 pour un projet Web local (différents chemins d’accès via le code mais a la même interface externe et le comportement).|Comportement attendu commun.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)