---
title: 'Zone de test 4 : archiver | Microsoft Docs'
description: Cette zone de test du plug-in de contrôle de code source traite de l’envoi d’éléments mis à jour à la Banque des versions à l’aide de la commande Archiver.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b8de88b75b7013b75a35c9e92dc662598185e92b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080552"
---
# <a name="test-area-4-check-in"></a>Zone de test 4 : Archiver
Cette zone de test du plug-in de contrôle de code source traite de l’envoi d’éléments mis à jour à la Banque des versions via la commande **Archiver** .

## <a name="command-menu-access"></a>Accès au menu commande
 Les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chemins d’accès au menu de l’environnement de développement intégré suivants sont utilisés dans les cas de test.

##### <a name="check-in"></a>Enregistrer :
 **Fichier**, **contrôle de code source**, **Archiver**.

 **Fichier**, **Archiver**.

 Menu contextuel, **Archiver**.

## <a name="common-expected-behavior"></a>Comportement attendu courant

- Les projets et les fichiers ajoutés à une solution ou à un projet sous contrôle de code source s’affichent dans la boîte de dialogue **Archiver** et la fenêtre **archivages en attente** .

- Après l’archivage, les éléments ajoutés apparaissent dans le contrôle de code source.

- Après l’archivage, les versions des éléments mis à jour sont correctement gérées dans le magasin.

## <a name="test-cases"></a>Cas de test
 Les éléments suivants sont des cas de test spécifiques pour la zone de test d’archivage.

### <a name="case-4a-modified-items"></a>Cas 4a : éléments modifiés
 Décrit l’utilisation de l’action archiver pour mettre à jour un fichier sous contrôle de code source qui a été modifié.

|Action|Étapes de test|Résultats attendus à vérifier|
|------------|----------------|--------------------------------|
|Modifier un fichier texte qui a été extrait, archiver uniquement un fichier (boîte **de dialogue Archiver** )|1. Créez un projet avec un fichier texte.<br />2. Ajoutez la solution au contrôle de code source.<br />3. extraire et modifier le fichier texte.<br />4. archiver via la boîte de dialogue Archiver (**fichier**, **contrôle de code source**, **Archiver**).|Comportement attendu courant.|
|Modifier un fichier texte qui a été extrait, archiver uniquement un fichier (fenêtre **archivages en attente** )|1. Créez un projet avec un fichier texte.<br />2. Ajoutez la solution au contrôle de code source.<br />3. extraire et modifier le fichier texte.<br />4. archiver via la fenêtre **archivages en attente** .|Comportement attendu courant.|

### <a name="case-4b-adding-files"></a>Cas 4b : ajout de fichiers
 Lorsque vous ajoutez un fichier à un projet ou à un élément dans une solution, le projet ou la solution doit également changer. Par conséquent, le fichier parent est également extrait et doit être archivé pour terminer l’addition.

|Action|Étapes de test|Résultats attendus à vérifier|
|------------|----------------|--------------------------------|
|Ajouter un fichier texte et archiver tout (boîte **de dialogue Archiver** )|1. Créez un nouveau projet.<br />2. Ajoutez la solution au contrôle de code source.<br />3. Ajoutez un fichier texte au projet.<br />4. acceptez l’extraction du projet si vous y êtes invité.<br />5. Sélectionnez la solution dans **Explorateur de solutions**.<br />6. archiver dans la boîte de dialogue **Archiver** .|Comportement attendu courant.|
|Ajouter un fichier texte et archiver tout (fenêtre **archivages en attente** )|1. Créez un nouveau projet.<br />2. Ajoutez la solution au contrôle de code source.<br />3. Ajoutez un fichier texte au projet.<br />4. acceptez l’extraction du projet si vous y êtes invité.<br />5. archiver la solution à partir de la fenêtre **archivages en attente** .|Comportement attendu courant|

### <a name="case-4c-adding-projects"></a>Cas 4C : ajout de projets
 Lorsque vous ajoutez un projet à une solution, la solution doit également changer. Par conséquent, le fichier solution est également extrait et doit être archivé pour terminer l’ajout.

|Action|Étapes de test|Résultats attendus à vérifier|
|------------|----------------|--------------------------------|
|Ajouter un projet à une solution vide sous contrôle de code source (boîte **de dialogue Archiver** )|1. Créez une solution vide.<br />2. Ajoutez la solution au contrôle de code source.<br />3. Ajoutez un nouveau projet.<br />4. acceptez l’extraction de la solution si vous y êtes invité.<br />5. archiver dans la boîte de dialogue **Archiver** .|Comportement attendu courant.|
|Ajouter un projet à une solution vide sous contrôle de code source (fenêtre **archivages en attente** )|1. Créez une solution vide.<br />2. Ajoutez la solution au contrôle de code source.<br />3. Ajoutez un nouveau projet.<br />4. acceptez l’extraction de la solution si vous y êtes invité.<br />5. archiver la solution à partir de la fenêtre **archivages en attente** .|Comportement attendu courant.|

## <a name="see-also"></a>Voir aussi
- [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
