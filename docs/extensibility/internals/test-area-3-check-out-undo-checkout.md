---
title: 'Zone d’essai 3: Départ pour les dénudés (fr) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, checkout
- source control plug-ins, undo checkout
- source control [Visual Studio SDK], checking out
- source control [Visual Studio SDK], undo checkout
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5365da1e342df5aea9c1b1cd2ae5a446baea57f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704619"
---
# <a name="test-area-3-check-outundo-checkout"></a>Zone d’essai 3: Départ/Annuler
Cette zone d’essai plug-in de contrôle des sources couvre l’édition et le retour des éléments du magasin de version via les commandes **Check Out** et **Undo Checkout.**

**Check Out**: Marque un article dans le magasin de version tel qu’il est vérifié, modifie la copie locale pour lire/écrire.

**Undo Checkout**: Marque un article dans le magasin de version comme enregistré, retourne la copie locale à l’état avant le départ (selon les options).

## <a name="command-menu-access"></a>Accès au menu de commande

Les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] parcours de menu intégrés suivants sont utilisés dans les cas d’essai.

##### <a name="check-out"></a>Modifier :

- **Fichier**, **Contrôle source**, **Check Out**.

- **Fichier**, **Check Out**.

- Menu raccourci, **Départ**.

- Décrochage : **Fichier**, **Contrôle source**, Départ **annuler**.

## <a name="common-expected-behavior"></a>Comportement attendu commun

- Après l’opération de départ, le fichier cible(s) et/ou le dossier(s) sont marqués comme vérifiés dans le magasin de version.

- Le magasin de version attribue la caisse à l’utilisateur correct.

- L’heure et la date de la caisse sont correctes (selon les paramètres de l’utilisateur).

## <a name="test-cases"></a>Cas de test

Voici des cas de test spécifiques pour la zone d’essai Checkout/Undo Checkout.

### <a name="case-3a-check-out"></a>Cas 3a: Check Out

Cette section met l’accent sur le fonctionnement de la commande de départ.

|Action|Étapes d’essai|Résultats attendus pour vérifier|
|------------|----------------|--------------------------------|
|Découvrez Exclusive (COE) un projet client|1. Créer un projet client.<br />2. Ajouter la solution au contrôle des sources.<br />3. Découvrez l’ensemble du projet exclusivement (**Fichier**, **Check Out**).|Le départ se produit.|
|Découvrez Exclusive (COE) un système de fichiers ou un projet Web local de l’IIS|1. Définir la connexion du serveur Web pour classer la part dans **les outils,** **les options**, **les projets**, **les paramètres Web**.<br />2. Créer un projet Web.<br />3. Ajouter la solution au contrôle des sources.<br />4. Découvrez l’ensemble du projet exclusivement (**Fichier**, **Contrôle source**, Check **Out**).|Le départ se produit.|
|Consultez les éléments de solution dans une solution (nouvelle méthode de traitement d’autres fichiers)|1. Créer une solution vierge.<br />2. Ajouter la solution au contrôle des sources.<br />3. Consultez la solution.<br />4. Ajouter plusieurs éléments de solution.<br />5. Vérifiez tous les éléments nouvellement ajoutés.<br />6. Sélectionnez plusieurs éléments de solution.<br />7. Découvrez les éléments sélectionnés (Menu raccourci, **Check Out**).|Les fichiers sélectionnés sont vérifiés.|
|Consultez la version locale (si plug-in sous test prend en charge cette fonctionnalité)|1. Utilisateur 1 : Créez un projet client.<br />2. Utilisateur 1 : Ajoutez la solution au contrôle source.<br />3. Utilisateur 2 : Ouvrez la solution du contrôle source à un autre endroit.<br />4. Utilisateur 2 : Consultez un fichier.<br />5. Utilisateur 2 : Modifier le fichier.<br />6. Utilisateur 2 : Vérifiez dans le fichier.<br />7. Utilisateur 1: Consultez la version locale du fichier (Vérifiez **l’option Check Out Local Version** avancée dans la boîte de dialogue Check **Out).**|La version locale du fichier est vérifiée.<br /><br /> Les modifications apportées par l’utilisateur 2 ne sont pas appliquées au fichier Utilisateur 1.|

### <a name="case-3b-disconnected-check-out"></a>Cas 3b: Déconnecté Check out

L’utilisation en mode déconnecté permet aux utilisateurs un certain niveau de support de contrôle source continu lorsqu’ils ne sont pas attachés directement à un magasin de version. Cela se fait en cachant localement toutes les informations pertinentes sur la solution et les projets enrôlés.

Les opérations de départ exclusives ne peuvent se produire que lorsqu’elles sont connectées au magasin de contrôle source. Les opérations de vérification partagée peuvent se produire à tout moment, qu’elles soient connectées ou déconnectées. Par conséquent, lorsqu’il est déconnecté du magasin de versions, seule la commande **Check Out Shared** (COS) est activée. Bien que déconnecté, **Undo Checkout** est désactivé parce que l’ancienne version ne peut pas être récupérée pour remplacer les modifications apportées par l’utilisateur.

Lorsque l’utilisateur se reconnecte au magasin de versions, les états de caisse de toutes les solutions et projets enrôlés sont synchronisés. Cela fait les mises à jour nécessaires au magasin pour les caisses que l’utilisateur a effectuées. Une fois que la synchronisation s’est produite, l’utilisateur est en mesure de continuer à travailler normalement (connecté).

#### <a name="expected-behavior"></a>Comportement attendu

- Impossible **d’utiliser Check Out Exclusivement** commande lorsqu’il est déconnecté du magasin de version.

- Impossible **d’utiliser la commande Undo Checkout** lorsqu’il est déconnecté du magasin de versions.

- **Les** commandes partagées Check Out fonctionnent.

|Action|Étapes d’essai|Résultats attendus pour vérifier|
|------------|----------------|--------------------------------|
|Bien que déconnecté, consultez un fichier, puis connectez-vous pour la synchronisation|1. Déconnectez un projet contrôlé à l’aide de la boîte de dialogue Change Source Control **(Fichier**, **Contrôle source**, **Changement de contrôle des sources**).<br />2. Vérifiez un fichier.<br />3. Cliquez sur Check Out (déconnecté) dans la boîte de dialogue d’avertissement.<br />4. Modifier le fichier.<br />5. Connectez-vous à l’aide de la boîte de dialogue Change Source Control.<br />6. Obtenez la dernière version du fichier édité.|Comportement attendu commun|

### <a name="case-3c-query-editquery-save-qeqs"></a>Cas 3c: Requête Edit/Requête Save (QEQS)
 Les éléments sous contrôle source sont suivis pour les modifications, les modifications et les sauvegardes pour aider les utilisateurs à gérer facilement leurs fichiers. Lorsqu’un élément contrôlé « enregistré » est modifié, QEQS intercepte la tentative de modification et demande à l’utilisateur s’il veut vérifier le fichier pour le modifier. Selon **les paramètres Tools**, **Options,** l’utilisateur est soit obligé de consulter le fichier afin de modifier ou peut être autorisé à modifier une copie dans la mémoire et vérifier plus tard. Si le réglage **des outils,** **options** de l’utilisateur n’est pas configuré pour afficher la boîte de dialogue de départ et pour le vérifier, alors que l’utilisateur effectue son montage, le fichier vérifie automatiquement, chaque fois que possible.

#### <a name="expected-behavior"></a>Comportement attendu

- Après l’opération de départ, le fichier cible(s) et/ou le dossier(s) sont marqués comme vérifiés dans le magasin de version.

- Le magasin de version attribue le check out à l’utilisateur correct.

- L’heure et la date du check out sont correctes (selon les paramètres de l’utilisateur).

- La copie locale du fichier cible ou du dossier est rédigeable.

|Action|Étapes d’essai|Résultats attendus pour vérifier|
|------------|----------------|--------------------------------|
|Modifier le fichier texte qui est enregistré|1. Créer un nouveau projet contenant un fichier texte.<br />2. Ajouter la solution au contrôle des sources.<br />3. Définir **des outils**, **options**, contrôle **des sources**, autoriser les fichiers à **être édités lors de la lecture uniquement sur le disque** à non vérifié.<br />4. Définir **des outils**, **Options**, **Contrôle source**, Prompt pour **vérifier** dans le **moment coché dans les fichiers sont édités** boîte combo.<br />5. Définir **des outils**, **Options**, **Contrôle source**, Prompt pour **vérifier** dans le moment enregistré dans les fichiers **sont enregistrés** boîte combo.<br />6. Ouvrez le fichier texte dans l’éditeur, essayez de taper du nouveau texte dans le fichier. Si cette étape réussit, continuez à passer à l’étape suivante.<br />7. Cliquez sur **Annuler** dans le **Check out pour Modifier** la boîte de dialogue. Si cette étape réussit, continuez à passer à l’étape suivante.<br />8. Définir des **outils**, **options**, contrôle **des sources**, autoriser les fichiers à **être édités lors de la lecture uniquement sur le disque** à vérifier.<br />9. Ouvrir le fichier de projet en éditeur, tenter de taper du nouveau texte dans le fichier. Si cette étape réussit, continuez à passer à l’étape suivante.<br />10. Cliquez sur **Modifier Edit** dans le Check out **pour Modifier** la boîte de dialogue. Si cette étape réussit, continuez à passer à l’étape suivante.<br />11. Modifier le fichier texte et tenter de l’enregistrer.|`Result of step 6:`<br /><br /> Découvrez la boîte de dialogue Edit.<br /><br /> `Result of step 7:`<br /><br /> Le fichier est inchangé.<br /><br /> `Result of step 9:`<br /><br /> Découvrez la boîte de dialogue Edit.<br /><br /> `Result of step 10:`<br /><br /> Vous pouvez modifier le fichier de projet en mémoire.<br /><br /> `Result of step 11:`<br /><br /> Sur l’enregistrement, le Check out sur enregistrer la boîte de dialogue apparaît.|
|Modifier un fichier de solution qui est enregistré|Répétez les étapes décrites lors du test précédent, mais au lieu de modifier un fichier texte, modifiez la solution en modifiant les propriétés de la solution.|Identique à l’essai précédent|
|Modifier un fichier de projet qui est enregistré|Répétez les étapes décrites lors du test précédent, mais au lieu de modifier un fichier texte, modifiez le projet en modifiant les propriétés du projet.|Comme lors du test précédent.|

### <a name="case-3d-silent-check-out"></a>Cas 3d: Silent Check Out
 Cette sous-zone couvre les scénarios de check-out où la boîte de dialogue **Check Out** n’apparaît pas par outils de l’utilisateur , **Options**, **Paramètres de contrôle des sources**. **Tools**

#### <a name="expected-behavior"></a>Comportement attendu

- Après l’opération de départ, le fichier cible(s) et/ou le dossier(s) sont marqués comme vérifiés dans le magasin de version.

- Le magasin de version attribue le check out à l’utilisateur correct.

- L’heure et la date du check out sont correctes (selon les paramètres de l’utilisateur).

- La copie locale du fichier cible ou du dossier est rédigeable.

|Action|Étapes d’essai|Résultats attendus pour vérifier|
|------------|----------------|--------------------------------|
|Caisse silencieuse pour un fichier|1. Définir **des outils**, **options**, contrôle **des sources** pour les fichiers de caisse automatiquement **sur modifier**.<br />2. Créer un nouveau projet avec un fichier.<br />3. Ajouter la solution au contrôle des sources.<br />4. Consultez le fichier.|Le fichier est vérifié silencieusement (pas d’interface utilisateur).|
|Caisse silencieuse pour un projet|1. Définir **des outils**, **options**, contrôle **des sources** pour les fichiers de caisse automatiquement **sur modifier**.<br />2. Créer un nouveau projet.<br />3. Ajouter la solution au contrôle des sources.<br />4. Consultez le projet.|Le fichier est vérifié silencieusement (pas d’interface utilisateur).|

### <a name="case-3e-undo-check-out"></a>Cas 3e: Annuler Check Out
 **Annuler Check Out** est utilisé pour annuler l’état vérifié d’un fichier et éviter de vérifier les modifications apportées au fichier.

#### <a name="expected-behavior"></a>Comportement attendu

- La valeur par défaut est basée sur le **paramètre Check out Local Version** de l’utilisateur. Si l’utilisateur a choisi de vérifier la version locale, alors la valeur par défaut pour la caisse annuler est de toujours revenir à la version vérifiée.

- Lors de l’acceptation de l’annulation, les icônes de **Solution Explorer** sont mises à jour pour les fichiers affectés et l’élément est supprimé de la fenêtre **Checkins en attente.**

|Action|Étapes d’essai|Résultats attendus pour vérifier|
|------------|----------------|--------------------------------|
|Annuler la caisse d’un seul fichier qui est vérifié exclusivement|1. Créer un projet client.<br />2. Ajouter la solution au contrôle des sources.<br />3. Consultez un fichier exclusivement.<br />4. Modifier le fichier.<br />5. Annuler la caisse (**Fichier**, **Contrôle source**, **Undo Checkout**).|Comportement attendu commun.|
|Annuler la caisse d’un seul fichier qui est vérifié partagé|1. Créer un projet client.<br />2. Ajouter la solution au contrôle des sources.<br />3. Consultez un fichier partagé.<br />4. Modifier le fichier.<br />5. Annuler la caisse (**Fichier**, **Contrôle source**, **Undo Checkout**).|Comportement attendu commun.|
|Annuler la vérification d’un projet après l’ajout de fichiers au projet|1. Créer un nouveau projet et l’ajouter au contrôle des sources.<br />2. Consultez le projet.<br />3. Ajouter un fichier au projet.<br />4. Annuler la vérification du projet.|Le fichier ajouté est supprimé du projet dans Solution Explorer.<br /><br /> Le projet n’est plus vérifié.|
|Annuler la vérification d’un projet après la suppression du fichier(s) du projet|1. Créer un nouveau projet et l’ajouter au contrôle des sources.<br />2. Consultez le projet.<br />3. Supprimer un fichier du projet.<br />4. Annuler la vérification du projet.|Le fichier supprimé apparaît dans Solution Explorer.<br /><br /> Le projet n’est plus vérifié.|

## <a name="see-also"></a>Voir aussi
- [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
