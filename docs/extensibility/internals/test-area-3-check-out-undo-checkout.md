---
title: 'Zone de test 3 : extraire-annuler l’extraction | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704619"
---
# <a name="test-area-3-check-outundo-checkout"></a>Zone de test 3 : Extraire/Annuler l’extraction
Cette zone de test du plug-in de contrôle de code source couvre la modification et le rétablissement des éléments de la Banque des versions via les commandes **extraire** et **Annuler l’extraction** .

**Extraire**: marque un élément de la Banque des versions comme extrait, modifie la copie locale en lecture/écriture.

**Annuler l’extraction**: marque un élément dans la Banque des versions comme archivé, restaure la copie locale à l’état antérieur à l’extraction (en fonction des options).

## <a name="command-menu-access"></a>Accès au menu commande

Les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chemins d’accès au menu de l’environnement de développement intégré suivants sont utilisés dans les cas de test.

##### <a name="check-out"></a>Modifier :

- **Fichier**, **contrôle de code source**, **extraire**.

- **Fichier**, **extraire**.

- Menu contextuel, **extraire**.

- Annuler l’extraction : **fichier**, **contrôle de code source**, **Annuler l’extraction**.

## <a name="common-expected-behavior"></a>Comportement attendu courant

- Après l’opération d’extraction, les fichiers et/ou dossiers cibles sont marqués comme extraits dans la Banque des versions.

- La Banque des versions attribut l’extraction à l’utilisateur approprié.

- La date et l’heure de l’extraction sont correctes (selon les paramètres de l’utilisateur).

## <a name="test-cases"></a>Cas de test

Les éléments suivants sont des cas de test spécifiques pour la zone de test extraction/annulation de l’extraction.

### <a name="case-3a-check-out"></a>Cas 3a : extraire

Cette section se concentre sur le fonctionnement de la commande d’extraction.

|Action|Étapes de test|Résultats attendus à vérifier|
|------------|----------------|--------------------------------|
|Extraire un projet client en mode exclusif (COE)|1. Créez un projet client.<br />2. Ajoutez la solution au contrôle de code source.<br />3. Vérifiez l’intégralité du projet exclusivement (**fichier**, **extraire**).|L’extraction se produit.|
|Extraire en mode exclusif (COE) un système de fichiers ou un projet Web IIS local|1. Définissez la connexion au serveur Web sur le partage de fichiers dans **Outils**, **options**, **projets**, **paramètres Web**.<br />2. Créez un projet Web.<br />3. Ajoutez la solution au contrôle de code source.<br />4. Vérifiez l’intégralité du projet exclusivement (**fichier**, **contrôle de code source**, **extraire**).|L’extraction se produit.|
|Extraire les éléments de solution dans une solution (nouvelle méthode pour gérer d’autres fichiers)|1. Créez une solution vide.<br />2. Ajoutez la solution au contrôle de code source.<br />3. consultez la solution.<br />4. ajoutez plusieurs éléments de solution.<br />5. archivez tous les éléments qui viennent d’être ajoutés.<br />6. Sélectionnez plusieurs éléments de solution.<br />7. consultez les éléments sélectionnés (menu contextuel, **extraire**).|Les fichiers sélectionnés sont extraits.|
|Extraire la version locale (si le plug-in test prend en charge cette fonctionnalité)|1. utilisateur 1 : créer un projet client.<br />2. utilisateur 1 : ajouter la solution au contrôle de code source.<br />3. utilisateur 2 : Ouvrez la solution à partir du contrôle de code source vers un autre emplacement.<br />4. utilisateur 2 : extraire un fichier.<br />5. utilisateur 2 : modifiez le fichier.<br />6. utilisateur 2 : archiver le fichier.<br />7. utilisateur 1 : extraire la version locale du fichier (consultez l’option avancé de la **version locale** de l’extraction dans la boîte de dialogue **extraire** ).|La version locale du fichier est extraite.<br /><br /> Les modifications apportées par l’utilisateur 2 ne sont pas appliquées au fichier utilisateur 1.|

### <a name="case-3b-disconnected-check-out"></a>Cas 3b : extraction déconnectée

Le fonctionnement en mode déconnecté permet aux utilisateurs d’effectuer un certain niveau de prise en charge du contrôle de code source lorsqu’ils ne sont pas attachés directement à une banque des versions. Pour ce faire, il faut mettre en cache localement toutes les informations pertinentes sur la solution et les projets inscrits.

Les opérations d’extraction exclusive ne peuvent se produire qu’en cas de connexion au magasin de contrôle de code source. Les opérations d’extraction partagées peuvent se produire à tout moment, qu’elles soient connectées ou déconnectées. Par conséquent, une fois déconnectée de la Banque des versions, seule la commande **extraire les Télépartages** (COS) est activée. Lorsqu’elle est déconnectée, l’annulation de l' **extraction** est désactivée, car l’ancienne version ne peut pas être récupérée pour remplacer les modifications apportées par l’utilisateur.

Lorsque l’utilisateur se reconnecte à la Banque des versions, les États d’extraction de tous les projets et solutions inscrites sont synchronisés. Cela effectue les mises à jour nécessaires du magasin pour les extractions effectuées par l’utilisateur. Une fois la synchronisation terminée, l’utilisateur peut continuer à fonctionner normalement (connecté).

#### <a name="expected-behavior"></a>Comportement attendu

- Impossible d’utiliser la commande **extraire en mode exclusif** quand elle est déconnectée de la Banque des versions.

- Impossible d’utiliser la commande **Annuler l’extraction** lorsqu’elle est déconnectée de la Banque des versions.

- La commande d’extraction **partagée** fonctionne.

|Action|Étapes de test|Résultats attendus à vérifier|
|------------|----------------|--------------------------------|
|En cas de déconnexion, retirez un fichier, puis connectez-vous pour la synchronisation|1. Déconnectez un projet contrôlé à l’aide de la boîte de dialogue Modifier le contrôle de code source (**fichier**, **contrôle de code source**, **modifier le contrôle de code source**).<br />2. Vérifiez le fichier.<br />3. cliquez sur extraire (déconnecté) dans la boîte de dialogue d’avertissement.<br />4. modifiez le fichier.<br />5. Connectez-vous à l’aide de la boîte de dialogue Modifier le contrôle de code source.<br />6. Procurez-vous la dernière version du fichier modifié.|Comportement attendu courant|

### <a name="case-3c-query-editquery-save-qeqs"></a>Cas 3C : modification de requête/requête d’enregistrement (provenant QEQS)
 Les éléments sous contrôle de code source sont suivis pour les modifications, les modifications et les enregistrements pour aider les utilisateurs à gérer facilement leurs fichiers. Lorsqu’un élément contrôlé qui est « archivé » est modifié, provenant QEQS intercepte la tentative de modification et demande à l’utilisateur s’il souhaite extraire le fichier pour le modifier. En fonction des **Outils**, des paramètres d' **options** , l’utilisateur est contraint d’extraire le fichier pour le modifier ou peut être autorisé à modifier une copie en mémoire et à extraire ultérieurement. Si le paramètre **Outils**et **options** de l’utilisateur n’est pas défini pour afficher la boîte de dialogue Extraire et si vous souhaitez simplement l’extraire, lorsque l’utilisateur effectue sa modification, le fichier est automatiquement extrait chaque fois que cela est possible.

#### <a name="expected-behavior"></a>Comportement attendu

- Après l’opération d’extraction, les fichiers et/ou dossiers cibles sont marqués comme extraits dans la Banque des versions.

- La Banque des versions attribut le contrôle à l’utilisateur approprié.

- L’heure et la date de l’extraction sont correctes (selon les paramètres de l’utilisateur).

- La copie locale du fichier ou dossier cible est accessible en écriture.

|Action|Étapes de test|Résultats attendus à vérifier|
|------------|----------------|--------------------------------|
|Modifier le fichier texte archivé|1. Créez un projet contenant un fichier texte.<br />2. Ajoutez la solution au contrôle de code source.<br />3. Définissez les **Outils**, les **options**, **le contrôle de code source**, **autoriser la modification des fichiers en lecture seule sur le disque** à la désactivation.<br />4. définir les **Outils**, les **options**, **le contrôle de code source**, **demander l’extraction** dans la zone de liste déroulante quand les **fichiers archivés sont modifiés** .<br />5. Définissez les **Outils**, les **options**, **le contrôle de code source**, **invite à extraire** dans la zone de liste déroulante **quand les fichiers archivés sont enregistrés** .<br />6. Ouvrez le fichier texte dans l’éditeur, puis essayez de taper un nouveau texte dans le fichier. Si cette étape se déroule correctement, passez à l’étape suivante.<br />7. cliquez sur **Annuler** dans la boîte **de dialogue Extraire pour modification** . Si cette étape se déroule correctement, passez à l’étape suivante.<br />8. définir les **Outils**, les **options**, **le contrôle de code source**, **autoriser la modification des fichiers en lecture seule sur le disque** à la vérification.<br />9. ouvrir le fichier projet dans l’éditeur, essayer de taper un nouveau texte dans le fichier. Si cette étape se déroule correctement, passez à l’étape suivante.<br />10. cliquez sur **modifier** dans la boîte **de dialogue Extraire pour modification** . Si cette étape se déroule correctement, passez à l’étape suivante.<br />11. modifiez le fichier texte et essayez de l’enregistrer.|`Result of step 6:`<br /><br /> La boîte de dialogue Extraire pour modification s’affiche.<br /><br /> `Result of step 7:`<br /><br /> Le fichier est inchangé.<br /><br /> `Result of step 9:`<br /><br /> La boîte de dialogue Extraire pour modification s’affiche.<br /><br /> `Result of step 10:`<br /><br /> Vous pouvez modifier le fichier projet en mémoire.<br /><br /> `Result of step 11:`<br /><br /> Lors de l’enregistrement, la boîte de dialogue extraire à l’enregistrement s’affiche.|
|Modifier un fichier solution archivé|Répétez les étapes décrites dans la section test précédent, mais au lieu de modifier un fichier texte, modifiez la solution en modifiant les propriétés de la solution.|Identique au test précédent|
|Modifier un fichier projet archivé|Répétez les étapes décrites dans la section test précédent, mais au lieu de modifier un fichier texte, modifiez Project en modifiant les propriétés du projet.|Identique au test précédent.|

### <a name="case-3d-silent-check-out"></a>Cas 3D : extraction en mode silencieux
 Cette sous-zone aborde les scénarios d’extraction dans lesquels la boîte de dialogue **extraire** n’apparaît pas pour les **Outils**, les **options**et les paramètres de **contrôle de code source**de l’utilisateur.

#### <a name="expected-behavior"></a>Comportement attendu

- Après l’opération d’extraction, les fichiers et/ou dossiers cibles sont marqués comme extraits dans la Banque des versions.

- La Banque des versions attribut le contrôle à l’utilisateur approprié.

- L’heure et la date de l’extraction sont correctes (selon les paramètres de l’utilisateur).

- La copie locale du fichier ou dossier cible est accessible en écriture.

|Action|Étapes de test|Résultats attendus à vérifier|
|------------|----------------|--------------------------------|
|Extraction silencieuse d’un fichier|1. Définissez les **Outils**, les **options**, **le contrôle de code source** pour **valider automatiquement les fichiers lors de la modification**.<br />2. Créez un projet avec un fichier.<br />3. Ajoutez la solution au contrôle de code source.<br />4. consultez le fichier.|Le fichier est extrait en mode silencieux (aucune interface utilisateur).|
|Extraction silencieuse d’un projet|1. Définissez les **Outils**, les **options**, **le contrôle de code source** pour **valider automatiquement les fichiers lors de la modification**.<br />2. Créez un nouveau projet.<br />3. Ajoutez la solution au contrôle de code source.<br />4. consultez le projet.|Le fichier est extrait en mode silencieux (aucune interface utilisateur).|

### <a name="case-3e-undo-check-out"></a>Cas 3e : annuler l’extraction
 L' **option Annuler** l’extraction est utilisée pour annuler l’état d’extraction d’un fichier et éviter d’archiver les modifications apportées au fichier.

#### <a name="expected-behavior"></a>Comportement attendu

- La valeur par défaut est basée sur le paramètre de **version locale d’extraction** de l’utilisateur. Si l’utilisateur a choisi d’extraire la version locale, la valeur par défaut pour annuler l’extraction consiste à toujours revenir à la version extraite.

- Après acceptation de l’annulation, les icônes de **Explorateur de solutions** sont mises à jour pour les fichiers affectés et l’élément est supprimé de la fenêtre **archivages en attente** .

|Action|Étapes de test|Résultats attendus à vérifier|
|------------|----------------|--------------------------------|
|Annuler l’extraction d’un seul fichier extrait en mode exclusif|1. Créez un projet client.<br />2. Ajoutez la solution au contrôle de code source.<br />3. extraire un fichier en mode exclusif.<br />4. modifiez le fichier.<br />5. annuler l’extraction (**fichier**, **contrôle de code source**, **Annuler l’extraction**).|Comportement attendu courant.|
|Annuler l’extraction d’un fichier unique qui est extrait partagé|1. Créez un projet client.<br />2. Ajoutez la solution au contrôle de code source.<br />3. extraire un fichier partagé.<br />4. modifiez le fichier.<br />5. annuler l’extraction (**fichier**, **contrôle de code source**, **Annuler l’extraction**).|Comportement attendu courant.|
|Annuler l’extraction d’un projet après l’ajout de fichier (s) au projet|1. Créez un projet et ajoutez-le au contrôle de code source.<br />2. consultez le projet.<br />3. Ajoutez un fichier au projet.<br />4. annulez l’extraction du projet.|Le fichier ajouté est supprimé du projet dans Explorateur de solutions.<br /><br /> Le projet n’est plus extrait.|
|Annuler l’extraction d’un projet après la suppression du ou des fichiers du projet|1. Créez un projet et ajoutez-le au contrôle de code source.<br />2. consultez le projet.<br />3. supprimer un fichier du projet.<br />4. annulez l’extraction du projet.|Le fichier supprimé apparaît sous le projet dans Explorateur de solutions.<br /><br /> Le projet n’est plus extrait.|

## <a name="see-also"></a>Voir aussi
- [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
