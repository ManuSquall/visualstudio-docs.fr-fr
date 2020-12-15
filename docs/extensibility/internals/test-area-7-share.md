---
title: 'Zone de test 7 : partage | Microsoft Docs'
description: Cette zone de test de contrôle de code source traite du partage d’éléments entre des emplacements à l’aide de la commande partager pour votre plug-in de contrôle de code source Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02593af854a9e68e7f4a6cc66f54452d3c3d3f94
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487606"
---
# <a name="test-area-7-share"></a>Zone de test 7 : Partager
Cette zone de test traite du partage d’éléments entre des emplacements via la commande de **partage** .

 Une opération hhare est la duplication apparente des fichiers et des éléments de dossier entre deux ou plusieurs emplacements au sein d’une hiérarchie de fichiers de contrôle de code source. La duplication ne se produit pas vraiment sur le serveur, mais l’utilisateur voit le même fichier dans deux ou plusieurs emplacements spécifiés. Chaque fois que des modifications sont apportées à l’un des éléments partagés, ces modifications apparaissent dans tous les autres emplacements partagés.

 Le partage dans des dossiers fonctionne si vous sélectionnez un dossier contenant au moins un fichier sous contrôle de code source. La commande de partage est désactivée dans les conditions suivantes :

- Si le dossier sélectionné est un dossier vide.

- S’il existe un dossier réel, mais qu’il ne contient aucun fichier de contrôle de code source.

- S’il existe un dossier virtuel, que les fichiers sous contrôle de code source y figurent ou non.

- S’il existe un projet Web de site distant.

## <a name="command-menu-access"></a>Accès au menu commande
 Les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chemins d’accès au menu de l’environnement de développement intégré suivants sont utilisés dans les cas de test.

 Partage :  -> partage de **contrôle de code source** de fichier -> .

## <a name="expected-behavior"></a>Comportement attendu

- Le fichier partagé s’affiche dans l’emplacement partagé.

- L’affichage de l’historique de la Banque des versions du contrôle de code source indique que ce ou ces fichiers sont partagés.

- La modification d’un fichier partagé modifie les deux emplacements du fichier.

## <a name="test-cases"></a>Cas de test
 Les éléments suivants sont des cas de test spécifiques pour la zone de test de partage.

|Action|Étapes de test|Résultats attendus à vérifier|
|------------|----------------|--------------------------------|
|Partager un fichier à partir d’un projet chargé sous contrôle de code source vers un autre projet chargé|1. Créez un nouveau projet.<br />2. Ajoutez un deuxième projet à la solution.<br />3. Créez un fichier dans le deuxième projet avec un nom qui n’est pas dans le premier projet.<br />4. Ajoutez la solution au contrôle de code source.<br />5. Sélectionnez le premier projet.<br />6. ouvrir la boîte de dialogue **partager** (partage de contrôle de  ->  **code source** du fichier  ->  ).<br />7. partagez le fichier du second projet vers le premier projet.<br />8 **. acceptez l’extraction si** vous y êtes invité.|Comportement attendu courant.|
|Partager un fichier d’un projet à un autre|1. Créez un nouveau projet.<br />2. Ajoutez-le au contrôle de code source.<br />3. Fermez la solution.<br />4. Créez un deuxième projet (nouvelle solution).<br />5. Ajoutez la solution au contrôle de code source.<br />6. Sélectionnez le projet.<br />7. Ouvrez la boîte de dialogue **partager** (partage de contrôle de  ->  **code source** du fichier  ->  ).<br />8. partagez un fichier du projet précédemment ajouté au projet ouvert.<br />9 **. acceptez l’extraction si** vous y êtes invité.|Comportement attendu courant.|
|Partager un fichier qui ne fait pas partie du projet à partir du contrôle de code source dans le projet actuellement chargé|1. Créez un nouveau projet.<br />2. Ajoutez la solution au contrôle de code source.<br />3. Ajoutez un fichier au contrôle de code source qui ne fait pas partie du projet ou de la solution.<br />4. Sélectionnez le projet et ouvrez la boîte de dialogue **partager** (partage de contrôle de  ->  **code source** du fichier  ->  ).<br />5. Sélectionnez dans la boîte de dialogue **partager** un fichier qui n’existe pas dans le projet ou la solution en cours et partagez-le.<br />6 **. acceptez l’extraction si** vous y êtes invité.|Le magasin de contrôle de code source a effectué une opération d’extraction, donc le fichier se trouve maintenant à l’emplacement local du projet.|
|Partager des fichiers dans le même projet dans un autre dossier|1. Sélectionnez **extraire automatiquement** dans **Outils**  ->  **options**  ->  **contrôle de code source**.<br />2. Créez un projet et ajoutez-le au contrôle de code source.<br />3. Ajoutez un dossier au projet.<br />4. Ajoutez un fichier au dossier et archivez-le dans le dossier.<br />5. Sélectionnez le dossier.<br />6. ouvrir la boîte de dialogue **partager** (partage de contrôle de  ->  **code source** du fichier  ->  ).<br />7. partage du fichier dans le dossier sélectionné.|Comportement attendu courant.<br /><br /> Le dossier doit être archivé avec un fichier avant de pouvoir être utilisé pour le partage.|
|Partager un dossier dans le projet chargé (récursif)|1. Créez un nouveau projet.<br />2. Ajoutez la solution au contrôle de code source.<br />3. Sélectionnez le projet.<br />4. Ouvrez la boîte de dialogue **partager** (partage de contrôle de  ->  **code source** du fichier  ->  ).<br />5. Sélectionnez un dossier.<br />6. partagez le dossier de manière récursive dans le projet.|Comportement attendu courant.|
|Partager plusieurs fichiers d’un projet à un autre|1. Créez un projet contenant plusieurs fichiers.<br />2. Ajoutez la solution au contrôle de code source.<br />3. Fermez la solution.<br />4. Créez un nouveau projet dans une nouvelle solution.<br />5. Ajoutez la solution au contrôle de code source.<br />6. Sélectionnez le projet.<br />7. Ouvrez la boîte de dialogue **partager** (partage de contrôle de  ->  **code source** du fichier  ->  ).<br />8. partagez plusieurs fichiers du projet créé précédemment avec le projet actuellement ouvert.|Comportement attendu courant.|

## <a name="see-also"></a>Voir aussi
- [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
