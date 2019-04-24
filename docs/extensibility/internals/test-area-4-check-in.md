---
title: 'Zone de test 4 : Archiver | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34d988f88787efc2f40b663ef2f22e6273055533
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60038710"
---
# <a name="test-area-4-check-in"></a>Zone de test 4 : Archiver
Cette zone de test plug-in de contrôle de code source couvre l’envoi des éléments mis à jour à la banque des versions via le **archiver** commande.

## <a name="command-menu-access"></a>Accès au Menu de commande
 Ce qui suit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] menu chemins d’environnement de développement intégré sont utilisés dans les cas de test.

##### <a name="check-in"></a>Date d'arrivée :
 **Fichier**, **contrôle de code Source**, **archiver**.

 **Fichier**, **archiver**.

 Menu contextuel, **archiver**.

## <a name="common-expected-behavior"></a>Comportement attendu commun

- Projets et fichiers ajoutés à une solution ou un projet sous contrôle de code source apparaissent dans le **archiver** boîte de dialogue et le **archivages en attente** fenêtre.

- Après l’archivage, les éléments ajoutés apparaissent dans le contrôle de code source.

- Après l’archivage, les éléments mis à jour sont correctement gérées dans le magasin.

## <a name="test-cases"></a>Cas de test
 Cas de test spécifiques pour la zone de test d’archivage sont les suivantes :

### <a name="case-4a-modified-items"></a>4 a case : Éléments modifiés
 Décrit l’utilisation de la vérification en action pour mettre à jour un fichier sous contrôle de code source qui a été modifié.

|Action|Étapes de test|Résultats attendus pour vérifier|
|------------|----------------|--------------------------------|
|Modifier un fichier texte qui a été extrait, archivez le fichier uniquement (**archiver** boîte de dialogue)|1.  Créer un nouveau projet avec un fichier texte.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Extraire et modifier le fichier texte.<br />4.  Archiver via la boîte de dialogue Archiver (**fichier**, **contrôle de code Source**, **archiver**).|Comportement attendu commun.|
|Modifier un fichier texte qui a été extrait, archivez le fichier uniquement (**archivages en attente** fenêtre)|1.  Créer un nouveau projet avec un fichier texte.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Extraire et modifier le fichier texte.<br />4.  Archiver le **archivages en attente** fenêtre.|Comportement attendu commun.|

### <a name="case-4b-adding-files"></a>4 b de cas : Ajout de fichiers
 Lorsque vous ajoutez un fichier à un projet ou un élément à une solution, le projet ou la solution doit également changer. Par conséquent, le fichier parent est également extrait et doit être archivé pour terminer l’ajout.

|Action|Étapes de test|Résultats attendus pour vérifier|
|------------|----------------|--------------------------------|
|Ajoutez un fichier texte et tout archiver (**archiver** boîte de dialogue)|1.  Créer un nouveau projet.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Ajoutez un fichier texte au projet.<br />4.  Accepter l’extraction du projet si vous y êtes invité.<br />5.  Sélectionnez la solution dans **l’Explorateur de solutions**.<br />6.  Archiver depuis le **archiver** boîte de dialogue.|Comportement attendu commun.|
|Ajoutez un fichier texte et tout archiver (**archivages en attente** fenêtre)|1.  Créer un nouveau projet.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Ajoutez un fichier texte au projet.<br />4.  Accepter l’extraction du projet si vous y êtes invité.<br />5.  Archiver la solution à partir de **archivages en attente** fenêtre.|Comportement attendu commun|

### <a name="case-4c-adding-projects"></a>Cas 4c : Ajout de projets
 Lorsque vous ajoutez un projet à une solution, la solution doit également changer. Par conséquent, le fichier solution est également extrait et doit être archivé pour terminer l’ajout.

|Action|Étapes de test|Résultats attendus pour vérifier|
|------------|----------------|--------------------------------|
|Ajouter un projet à une solution vide sous contrôle de code source (**archiver** boîte de dialogue)|1.  Créer une solution vide.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Ajouter un nouveau projet.<br />4.  Accepter l’extraction de la solution si vous y êtes invité.<br />5.  Archiver depuis le **archiver** boîte de dialogue.|Comportement attendu commun.|
|Ajouter un projet à une solution vide sous contrôle de code source (**archivages en attente** fenêtre)|1.  Créer une solution vide.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Ajouter un nouveau projet.<br />4.  Accepter l’extraction de la solution si vous y êtes invité.<br />5.  Archiver la solution à partir de **archivages en attente** fenêtre.|Comportement attendu commun.|

## <a name="see-also"></a>Voir aussi
- [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)