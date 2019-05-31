---
title: 'Zone de test 7 : Share | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b117bcf78d4644533f8931296e6f726281fe14e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327841"
---
# <a name="test-area-7-share"></a>Zone de test 7 : Partager
Cette zone de test couvre le partage des objets entre des emplacements via la **partage** commande.

 Une opération de hhare est la duplication apparente des fichiers et des éléments de dossier entre deux ou plusieurs emplacements au sein d’une hiérarchie de fichiers de contrôle de code source. Duplication ne survient pas réellement sur le serveur, mais l’utilisateur ne voit pas le même fichier dans deux ou plusieurs emplacements spécifiés. Chaque fois que les modifications sont apportées à l’un des éléments partagés, ces modifications apparaissent dans tous les autres emplacements partagés.

 Dans des dossiers de partage fonctionne si vous sélectionnez un dossier au moins un fichier sous contrôle de code source qu’il contient. La commande de partage est désactivée dans les conditions suivantes :

- Si le dossier sélectionné est un dossier vide.

- S’il existe un dossier réel, mais il ne contient aucun fichier de contrôle de source.

- S’il existe un dossier virtuel, que les fichiers sous contrôle de code source sont qu’il contient ou non.

- En l’absence d’un projet Web de Site distant.

## <a name="command-menu-access"></a>Accès au Menu de commande
 Ce qui suit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] menu chemins d’environnement de développement intégré sont utilisés dans les cas de test.

 Partager : **Fichier**->**contrôle de code Source**->**partage**.

## <a name="expected-behavior"></a>Comportement attendu

- Fichier partagé s’affiche dans un emplacement partagé.

- Affichage de la source contrôle version store historique affiche que les fichiers sont partagés.

- Modification d’un fichier partagé modifie les emplacements du fichier.

## <a name="test-cases"></a>Cas de test
 Voici les cas de test spécifiques pour la zone de test de partage.

|Action|Étapes de test|Résultats attendus pour vérifier|
|------------|----------------|--------------------------------|
|Partager un fichier à partir d’un projet chargé sous contrôle de code source à un autre projet chargé|1.  Créer un nouveau projet.<br />2.  Ajouter un deuxième projet à la solution.<br />3.  Créez un fichier dans le second projet avec un nom qui n’est pas dans le premier projet.<br />4.  Ajouter la solution au contrôle de code source.<br />5.  Sélectionnez le premier projet.<br />6.  Ouvrez **partage** boîte de dialogue (**fichier** -> **contrôle de code Source** -> **partage**).<br />7.  Partagez le fichier à partir du deuxième projet pour le premier projet.<br />8.  Accepter **Check Out** si vous y êtes invité.|Comportement attendu commun.|
|Partager un fichier à partir d’un projet vers un autre|1.  Créer un nouveau projet.<br />2.  Ajouter au contrôle de code source.<br />3.  Fermez la solution.<br />4.  Créer un deuxième projet (nouvelle solution).<br />5.  Ajouter la solution au contrôle de code source.<br />6.  Sélectionnez le projet.<br />7.  Ouvrez le **partage** boîte de dialogue (**fichier** -> **contrôle de code Source** -> **partage**).<br />8.  Partager un fichier à partir du projet précédemment ajouté au projet ouvert.<br />9. Accepter **Check Out** si vous y êtes invité.|Comportement attendu commun.|
|Partager un fichier ne fait pas partie du projet à partir du contrôle de code source dans le projet actuellement chargé.|1.  Créer un nouveau projet.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Ajouter un fichier de contrôle de code source qui ne fait pas partie du projet ou solution.<br />4.  Sélectionnez le projet et ouvrez le **partage** boîte de dialogue (**fichier** -> **contrôle de code Source** -> **partage**).<br />5.  Sélectionnez un fichier dans le **partager** boîte de dialogue qui ne pas exister dans le projet actuel ou la solution et le partager.<br />6.  Accepter **Check Out** si vous y êtes invité.|Le magasin de contrôle de code source a effectué une opération Get, par conséquent, le fichier est présent à l’emplacement local du projet.|
|Partager des fichiers dans le même projet vers un autre dossier|1.  Sélectionnez **extraire automatiquement** dans **outils** -> **Options** -> **contrôle de code Source**.<br />2.  Créer un nouveau projet et l’ajouter au contrôle de code source.<br />3.  Ajouter un dossier au projet.<br />4.  Ajouter un fichier dans le dossier et vérifiez dans le dossier.<br />5.  Sélectionnez le dossier.<br />6.  Ouvrez **partage** boîte de dialogue (**fichier** -> **contrôle de code Source** -> **partage**).<br />7.  Partager le fichier dans le dossier sélectionné.|Comportement attendu commun.<br /><br /> Avant de pouvoir être utilisé pour le partage, dossier doit être activé avec un fichier qu’il contient.|
|Partager un dossier dans le projet chargé, récursive|1.  Créer un nouveau projet.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Sélectionnez le projet.<br />4.  Ouvrez le **partage** boîte de dialogue (**fichier** -> **contrôle de code Source** -> **partage**).<br />5.  Sélectionnez un dossier.<br />6.  Partager le dossier de manière récursive dans le projet.|Comportement attendu commun.|
|Partager plusieurs fichiers à partir d’un projet vers un autre|1.  Créez un projet avec plusieurs fichiers.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Fermez la solution.<br />4.  Créer un nouveau projet dans une nouvelle solution.<br />5.  Ajouter la solution au contrôle de code source.<br />6.  Sélectionnez le projet.<br />7.  Ouvrez le **partage** boîte de dialogue (**fichier** -> **contrôle de code Source** -> **partage**).<br />8.  Partager plusieurs fichiers à partir du projet créé précédemment au projet actuellement ouvert.|Comportement attendu commun.|

## <a name="see-also"></a>Voir aussi
- [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)