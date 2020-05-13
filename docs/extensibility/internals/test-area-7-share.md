---
title: 'Zone d’essai 7 : Partager Microsoft Docs'
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
ms.openlocfilehash: fd4c48e94015d95f5e56d465cdbf98562108d3b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704403"
---
# <a name="test-area-7-share"></a>Zone de test 7 : Partager
Cette zone d’essai couvre le partage d’éléments entre les emplacements via la commande **Share.**

 Une opération de hhare est la duplication apparente de fichiers et d’éléments de dossier entre deux ou plusieurs emplacements dans une hiérarchie de fichiers de contrôle source. Duplication ne se produit pas vraiment sur le serveur, mais l’utilisateur ne voir le même fichier dans deux endroits spécifiés ou plus. Chaque fois que des modifications sont apportées à l’un des éléments partagés, ces modifications apparaissent dans tous les autres emplacements partagés.

 Partager dans les dossiers fonctionne si vous sélectionnez un dossier avec au moins un fichier sous contrôle source en elle. La commande d’actions est désactivée dans les conditions suivantes :

- Si le dossier sélectionné est un dossier vide.

- S’il y a un vrai dossier, mais il ne contient aucun fichier de contrôle source.

- S’il y a un dossier virtuel, que les fichiers sous contrôle source y soient ou non.

- S’il y a un projet Web de site à distance.

## <a name="command-menu-access"></a>Accès au menu de commande
 Les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] parcours de menu intégrés suivants sont utilisés dans les cas d’essai.

 Partager: **File**->**Source Control**->**Share**.

## <a name="expected-behavior"></a>Comportement attendu

- Le fichier partagé apparaît dans un emplacement partagé.

- L’affichage de l’historique du magasin de version de contrôle source montre que les fichiers sont partagés.

- L’édition d’un fichier partagé modifie les deux emplacements du fichier.

## <a name="test-cases"></a>Cas de test
 Ce qui suit sont des cas de test spécifiques pour la zone d’essai De partage.

|Action|Étapes d’essai|Résultats attendus pour vérifier|
|------------|----------------|--------------------------------|
|Partager un fichier d’un projet chargé sous contrôle source à un autre projet chargé|1. Créer un nouveau projet.<br />2. Ajouter un deuxième projet à la solution.<br />3. Créer un fichier dans le deuxième projet avec un nom qui n’est pas dans le premier projet.<br />4. Ajouter la solution au contrôle des sources.<br />5. Sélectionnez le premier projet.<br />6. Boîte de dialogue **Open Share** **(File** -> **Source Control** -> **Share**).<br />7. Partager le fichier du deuxième projet au premier projet.<br />8. **Acceptez Check Out** si vous êtes invité.|Comportement attendu commun.|
|Partager un fichier d’un projet à un autre|1. Créer un nouveau projet.<br />2. Ajoutez-le au contrôle des sources.<br />3. Fermez la solution.<br />4. Créer un deuxième projet (nouvelle solution.)<br />5. Ajouter la solution au contrôle des sources.<br />6. Sélectionnez le projet.<br />7. Ouvrez la boîte de dialogue **d’actions** ( Partage**de contrôle** -> de source**de** -> **fichiers**).<br />8. Partager un fichier du projet précédemment ajouté au projet ouvert.<br />9. **Acceptez Check Out** si vous êtes invité.|Comportement attendu commun.|
|Partager un fichier ne faisant pas partie du projet du contrôle source dans le projet actuellement chargé|1. Créer un nouveau projet.<br />2. Ajouter la solution au contrôle des sources.<br />3. Ajouter un fichier au contrôle de source qui ne fait pas partie du projet ou de la solution.<br />4. Sélectionnez le projet et ouvrez la boîte de dialogue **d’actions** ( Partage**de contrôle** -> des sources**de** -> **fichiers**).<br />5. Sélectionnez un fichier dans la boîte de dialogue **partager** qui n’existe pas dans le projet ou la solution en cours et partagez-le.<br />6. **Acceptez Check Out** si vous êtes invité.|Le magasin de contrôle source a effectué un Get, de sorte que le fichier est maintenant à l’emplacement local du projet.|
|Partager des fichiers dans le même projet à un dossier différent|1. Sélectionnez **Vérifiez automatiquement** dans **Tools** -> **Options** -> **Source Control**.<br />2. Créer un nouveau projet et l’ajouter au contrôle des sources.<br />3. Ajouter un dossier au projet.<br />4. Ajouter un fichier au dossier et enregistrer le dossier.<br />5. Sélectionnez le dossier.<br />6. Boîte de dialogue **Open Share** **(File** -> **Source Control** -> **Share**).<br />7. Partager le fichier dans le dossier sélectionné.|Comportement attendu commun.<br /><br /> Le dossier doit être enregistré avec un fichier en elle avant qu’il puisse être utilisé pour la part.|
|Partager un dossier dans le projet chargé — Recursif|1. Créer un nouveau projet.<br />2. Ajouter la solution au contrôle des sources.<br />3. Sélectionnez le projet.<br />4. Ouvrez la boîte de dialogue **d’actions** ( Partage**de contrôle** -> de source**de** -> **fichiers**).<br />5. Sélectionnez un dossier.<br />6. Partager le dossier de façon récursive dans le projet.|Comportement attendu commun.|
|Partager plusieurs fichiers d’un projet à un autre|1. Créer un nouveau projet avec plusieurs fichiers en elle.<br />2. Ajouter la solution au contrôle des sources.<br />3. Fermez la solution.<br />4. Créer un nouveau projet dans une nouvelle solution.<br />5. Ajouter la solution au contrôle des sources.<br />6. Sélectionnez le projet.<br />7. Ouvrez la boîte de dialogue **d’actions** ( Partage**de contrôle** -> de source**de** -> **fichiers**).<br />8. Partager plusieurs fichiers du projet déjà créé au projet actuellement ouvert.|Comportement attendu commun.|

## <a name="see-also"></a>Voir aussi
- [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
