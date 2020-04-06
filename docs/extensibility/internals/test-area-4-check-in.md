---
title: 'Zone d’essai 4 : Check In Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2386a217de228c5c47b467e6e083d978702927f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704575"
---
# <a name="test-area-4-check-in"></a>Zone de test 4 : Archiver
Cette zone d’essai plug-in de contrôle des sources couvre l’envoi d’articles mis à jour au magasin de version via la commande **Check In.**

## <a name="command-menu-access"></a>Accès au menu de commande
 Les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] parcours de menu intégrés suivants sont utilisés dans les cas d’essai.

##### <a name="check-in"></a>Enregistrer :
 **Fichier**, **Contrôle source**, **Check In**.

 **Fichier**, **Check In**.

 Menu raccourci, **Check In**.

## <a name="common-expected-behavior"></a>Comportement attendu commun

- Les projets et les fichiers ajoutés à une solution ou à un projet sous contrôle source apparaissent dans la boîte de dialogue **Check In** et la fenêtre **Checkins en attente.**

- Après l’enregistrement, les éléments ajoutés apparaissent dans le contrôle source.

- Après l’enregistrement, les articles mis à jour sont correctement versionnés dans le magasin.

## <a name="test-cases"></a>Cas de test
 Ce qui suit sont des cas de test spécifiques pour la zone d’essai Checkin.

### <a name="case-4a-modified-items"></a>Cas 4a : Articles modifiés
 Décrit l’utilisation de l’action de contrôle pour mettre à jour un fichier sous contrôle source qui a été modifié.

|Action|Étapes d’essai|Résultats attendus pour vérifier|
|------------|----------------|--------------------------------|
|Modifier un fichier texte qui a été vérifié, cocher dans le fichier seulement **(Check In** boîte de dialogue)|1. Créer un nouveau projet avec un fichier texte.<br />2. Ajouter la solution au contrôle des sources.<br />3. Vérifiez et modifiez le fichier texte.<br />4. Check in via la case Check In dialogue (**Fichier**, **Contrôle source**, Check **In**).|Comportement attendu commun.|
|Modifier un fichier texte qui a été vérifié, Vérifier le fichier uniquement (en attendant la fenêtre**Checkins)**|1. Créer un nouveau projet avec un fichier texte.<br />2. Ajouter la solution au contrôle des sources.<br />3. Vérifiez et modifiez le fichier texte.<br />4. Enregistrez-vous par la fenêtre **Checkins en attente.**|Comportement attendu commun.|

### <a name="case-4b-adding-files"></a>Cas 4b : Ajout de fichiers
 Lors de l’ajout d’un fichier à un projet ou d’un élément à une solution, le projet ou la solution doit également changer. Ainsi, le fichier parent est également vérifié et doit être enregistré pour compléter l’ajout.

|Action|Étapes d’essai|Résultats attendus pour vérifier|
|------------|----------------|--------------------------------|
|Ajouter un fichier texte et tout cocher **(Check In** dialog box)|1. Créer un nouveau projet.<br />2. Ajouter la solution au contrôle des sources.<br />3. Ajouter un fichier texte au projet.<br />4. Acceptez le départ du projet s’il est invité.<br />5. Sélectionnez la solution dans **Solution Explorer**.<br />6. Vérifiez dans la boîte de dialogue **Check In.**|Comportement attendu commun.|
|Ajouter un fichier texte et vérifier tout (en attendant la fenêtre**Checkins)**|1. Créer un nouveau projet.<br />2. Ajouter la solution au contrôle des sources.<br />3. Ajouter un fichier texte au projet.<br />4. Acceptez le départ du projet s’il est invité.<br />5. Vérifiez la solution à partir de la fenêtre **Checkins en attente.**|Comportement attendu commun|

### <a name="case-4c-adding-projects"></a>Cas 4c : Ajout de projets
 Lors de l’ajout d’un projet à une solution, la solution doit également changer. Ainsi, le fichier de solution est également vérifié et doit être enregistré pour compléter l’ajout.

|Action|Étapes d’essai|Résultats attendus pour vérifier|
|------------|----------------|--------------------------------|
|Ajouter un projet à une solution vierge sous contrôle source (**Check In** dialog box)|1. Créer une solution vierge.<br />2. Ajouter la solution au contrôle des sources.<br />3. Ajouter un nouveau projet.<br />4. Acceptez le départ de la solution si vous êtes invité.<br />5. Vérifiez dans la boîte de dialogue **Check In.**|Comportement attendu commun.|
|Ajouter un projet à une solution vierge sous contrôle source (en attendant la fenêtre**Checkins)**|1. Créer une solution vierge.<br />2. Ajouter la solution au contrôle des sources.<br />3. Ajouter un nouveau projet.<br />4. Acceptez le départ de la solution si vous êtes invité.<br />5. Vérifiez la solution à partir de la fenêtre **Checkins en attente.**|Comportement attendu commun.|

## <a name="see-also"></a>Voir aussi
- [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
