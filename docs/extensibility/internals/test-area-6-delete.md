---
title: 'Zone de test 6 : Supprimer de | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 97fc6ab9746e7ef2188c78dc77ec357f7d415a42
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140227"
---
# <a name="test-area-6-delete"></a>Tester la zone 6 : supprimer
Cette zone de plug-in de test de contrôle de code source couvre les actions de suppression.  
  
 Contrôle de code source répond pour supprimer des actions dans **l’Explorateur de solutions**.  
  
 Voici une liste d’éléments qui peuvent être supprimées :  
  
-   Fichiers  
  
-   Dossiers  
  
-   Projet  
  
 Selon le type de projet peut avoir l’option à **supprimer** le projet (laisse les fichiers sur le disque) ou **supprimer** le projet (supprime les fichiers sur disque). Des actions supprime le projet ou l’élément à partir de **l’Explorateur de solutions**.  
  
## <a name="expected-behavior"></a>Comportement attendu  
 Le comportement attendu pour les cas de test dans la zone de test delete est :  
  
-   Élément supprimé n’est plus visible dans **l’Explorateur de solutions**.  
  
-   Le parent de l’élément ou un projet supprimé est extrait en fonction des besoins (éventuellement avec une invite de commandes.)  
  
-   Une fois que vous supprimez un délai ou ajout d’un élément, il n’apparaît pas dans le **archivages en attente** fenêtre.  
  
-   L’élément existe dans le magasin de contrôle de code source, même après la suppression, encore et doive être supprimé manuellement.  
  
|Action|Étapes de test|Résultats attendus à vérifier|  
|------------|----------------|--------------------------------|  
|Supprimer un projet de client|1.  Créez un projet de client.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Supprimer l’ensemble du projet à partir de la solution|Comportement attendu commun.|  
|Suppression d’un fichier vide|1.  Créez un projet de client.<br />2.  Ajouter un fichier de zéro octet au projet.<br />3.  Ajouter la solution au contrôle de code source.<br />4.  Sélectionnez le fichier, supprimez-le.|Comportement attendu commun.|  
|Supprimer un dossier avec un fichier|1.  Créer la solution de projet unique.<br />2.  Ajouter un dossier.<br />3.  Ajouter un fichier dans le dossier.<br />4.  Ajouter la solution au contrôle de code source.<br />5.  Extraire le projet afin d’éviter les invites.<br />6.  Supprimez le dossier.|Comportement attendu commun.|  
|Supprimer un projet Web de système de fichiers|1.  Créez un projet Web de système de fichiers (utilisez le bouton Parcourir pour spécifier un chemin d’accès UNC).<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Supprimer l’ensemble du projet de la solution.<br />4.  Répétez les étapes 1 à 3 pour un projet Web local (chemins d’accès différents dans le code mais a la même interface externe et le comportement).|Comportement attendu commun.|  
|Supprimer un fichier à partir d’un projet Web de système de fichiers|1.  Créer un projet Web de système de fichiers.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Supprimer un fichier à partir du projet.<br />4.  Répétez les étapes 1 à 3 pour un projet Web local (chemins d’accès différents dans le code mais a la même interface externe et le comportement).|Comportement attendu commun.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)