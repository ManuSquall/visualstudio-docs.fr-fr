---
title: 'Zone d’essai 5 : Changement de contrôle des sources (fr) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d1c0df31fbecd532e6a5f7f317730cd995cd8225
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704522"
---
# <a name="test-area-5-change-source-control"></a>Zone de test 5 : Modifier le contrôle de code source
Cette zone d’essai plug-in de contrôle des sources couvre la modification du contrôle source via la commande **De contrôle des sources de** changement.

 **La** commande de contrôle des sources de modification fournit quatre fonctions de base pour l’utilisateur :

- **Lier:**

   Permet à un utilisateur d’établir ou de rétablir un lien de contrôle source entre une solution/projet et le magasin de versions.

- **Unbind:**

   Supprime un projet/solution du contrôle source sur une base par connexion.

- **Connectez/Déconnectez:**

  Bascule l’état connecté ou hors ligne de la solution contrôlée, qui est couverte dans la zone 3. Pour plus d’informations, voir [Zone d’essai 3: Check Out/Undo Checkout](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).

## <a name="command-menu-access"></a>Accès au menu de commande
 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] parcours intégré de menu environnement de développement suivant est utilisé dans les cas d’essai.

 Contrôle des sources de modification :**Fichier**, **Contrôle source**, Changement de **contrôle source**.

## <a name="test-cases"></a>Cas de test
 Voici des cas de test spécifiques pour la zone d’essai de commande **de contrôle des sources de changement.**

### <a name="case-5a-bind"></a>Cas 5a: Bind
 Bind permet à l’utilisateur d’ajouter des informations de contrôle de code source aux projets et solutions sélectionnés. L’utilisateur est généralement invité à identifier un projet sous contrôle source auquel ils doivent être ajoutés. L’utilisateur ne peut pas créer un nouveau projet en contrôle source dans le cadre de cette opération (contrairement à Add to Source Control).

| Action | Étapes d’essai | Résultats attendus pour vérifier |
| - | - | - |
| Lier à l’emplacement vide | 1. Créer un projet.<br />2. Ajouter la solution au contrôle des sources.<br />3. Open **Change Source Control** dialog box (**Fichier**, **Contrôle source**, Changement de contrôle **des sources**).<br />4. Cliquez **sur Unbind**.<br />5. Acceptez la boîte de dialogue d’avertissement si elle apparaît.<br />6. Sélectionnez tous les éléments.<br />7. Cliquez sur **Bind**.<br />8. Naviguez à un endroit vide dans un magasin de contrôle source.<br />9. Cliquez **sur OK** pour fermer la boîte de dialogue De contrôle de source **de changement.**<br />10. Cliquez **sur Continuer avec ces fixations** dans la boîte de dialogue de confirmation.<br />11. Cliquez **SUR OK** dans la boîte de dialogue d’avertissement si elle apparaît.<br />12. Vérifiez tout. Si cette étape réussit, continuez à passer à l’étape suivante.<br />13. Solution ouverte du contrôle source à un nouvel emplacement. | `Result from Step 12:`<br /><br /> Solution et projet sont liés et écrits à la nouvelle cible dans le magasin de version.<br /><br /> Les fichiers de solutions et de projet sont enregistrés.<br /><br /> La hiérarchie du projet de magasin de version correspond à la hiérarchie du dossier du projet sur disque.<br /><br /> `Result from Step 13:`<br /><br /> Tous les éléments du projet sont téléchargés. |
| Associez-le à l’emplacement qui est en phase avec le client | 1. Créer un projet.<br />2. Ajouter la solution au contrôle des sources.<br />3. Créer un doublement de la solution et du [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]projet dans le magasin de version (Partager et Branch si vous utilisez ).<br />4. Open **Change Source Control** dialog box (**Fichier**, **Contrôle source**, Changement de contrôle **des sources**).<br />5. Unbind All.<br />6. Cliquez **sur OK** pour fermer la boîte de dialogue De contrôle des sources de **changement.**<br />7. Réouverture de la boîte de dialogue **de contrôle des sources de** changement.<br />8. Sélectionnez tous.<br />9. Cliquez sur **Bind**.<br />10. Parcourir jusqu’à l’emplacement ramifié de la solution et du projet (à partir de l’étape 3)<br />11. Cliquez **sur OK** pour fermer la boîte de dialogue De contrôle des sources **de changement.**<br />12. Obtenez les dernières récursives pour tous les articles. | Le contenu du fichier après l’obtenir est le même qu’avant l’obtenir. |
| Associez-le à un endroit qui n’est pas synchronisé avec le client | 1. Créer un projet.<br />2. Ajouter la solution au contrôle des sources.<br />3. Créer un doublement de la solution et du [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]projet dans le magasin de version (Partager et Branch si vous utilisez ).<br />4. Modifier les fichiers du projet ramifié dans le magasin de versions.<br />5. Open **Change Source Control** dialog box (**Fichier**, **Contrôle source**, Changement de contrôle **des sources**).<br />6. Unbind tous.<br />7. Cliquez **sur OK** pour fermer la boîte de dialogue De contrôle de source de **changement.**<br />8. Réouverture de la boîte de dialogue **de contrôle des sources de** changement.<br />9. Sélectionnez tous.<br />10. Cliquez sur **Bind**.<br />11. Naviguez à l’emplacement ramifié pour la solution et le projet.<br />12. Cliquez **sur OK** pour fermer la boîte de dialogue De contrôle de source **de changement.**<br />13. Acceptez la boîte de dialogue d’avertissement si elle apparaît.<br />14. Obtenez les dernières récursives pour tous les articles. | Les fichiers qui ont été modifiés dans l’étape 4 sont également modifiés localement. |
| Solution de liaison qui n’a jamais été sous le contrôle source | 1. Créer un dossier vide dans le contrôle source.<br />2. Créer un projet client.<br />3. Open **Change Source Control** dialog box (**Fichier**, **Contrôle source**, Changement de contrôle **des sources**).<br />4. Lier la solution à l’emplacement vide dans le contrôle source.<br />5. Cliquez **sur OK** pour fermer la boîte de dialogue De contrôle de source **de changement.**<br />6. Cliquez **sur Continuer avec ces fixations** dans la boîte de dialogue de confirmation.<br />7. Cliquez **SUR OK** dans la boîte de dialogue d’avertissement si elle apparaît. | La solution est ajoutée au contrôle des sources.<br /><br /> La solution et le projet sont vérifiés. |
| Annuler la liaison | 1. Créer un projet.<br />2. Ajouter la solution au contrôle des sources.<br />3. Ouvrez la boîte de dialogue de contrôle de source de changement.<br />4. Unbind All.<br />5. Cliquez sur le bouton **OK** pour fermer la boîte de dialogue. Si cette étape réussit, continuez à passer à l’étape suivante.<br />6. Réuvrer la boîte de dialogue **de contrôle de source de changement.**<br />7. Se lier à un endroit sans rapport.<br />8. **Cliquez**annuler . | `Result from Step 5:`<br /><br /> La solution n’est plus sous contrôle source<br /><br /> `Result from Step 8:`<br /><br /> La solution n’est toujours pas sous contrôle source. |

### <a name="case-5b-unbind"></a>Cas 5b: Unbind
 Unbind supprime les informations de contrôle du code source des projets et de leur solution. Les projets et la solution concernés sont basés sur un mélange de sélection des utilisateurs et de la façon dont les éléments ont été ajoutés au contrôle des sources.

|Action|Étapes d’essai|Résultats attendus pour vérifier|
|------------|----------------|--------------------------------|
|Solution non contraignante contenant un système de fichiers ou un projet Web local de l’IIS et un projet client|1. Créer un système de fichiers ou un projet Web local de l’IIS.<br />2. Ajouter la solution au contrôle des sources.<br />3. Ajouter un nouveau projet client à la solution.<br />4. AcceptEz Check Out de la solution si vous êtes invité.<br />5. Ouvrez la boîte de dialogue de contrôle de source de **changement.**<br />6. Cliquez **sur Unbind**.<br />7. Cliquez **sur OK** pour fermer la boîte de dialogue.<br />8. Essayez de vérifier la solution, le projet, les éléments de solution, les éléments de projet.|La solution et les projets ne sont PAS sous contrôle source.<br /><br /> Les commandes de menu de contrôle des sources n’apparaissent pas.|
|Annuler Unbind|1. Créer un projet.<br />2. Ajouter la solution au contrôle des sources.<br />3. Ouvrez la boîte de dialogue de contrôle de source de **changement.**<br />4. Cliquez **sur Unbind tous**.<br />5. **Cliquez**annuler .|La solution est sous contrôle source.|

### <a name="case-5c-rebind"></a>Cas 5c: Rebind
 Rebind est simplement une combinaison de non contraignants et de liaison— le processus de rebinding d’un projet /solution qui était auparavant sous contrôle source et qui n’était pas lié.

|Action|Étapes d’essai|Résultats attendus pour vérifier|
|------------|----------------|--------------------------------|
|Solution et projets rebinés sans fermer la boîte de dialogue **Change Source Control**|1. Créer un projet.<br />2. Ajouter la solution au contrôle des sources.<br />3. Ouvrez la boîte de dialogue de contrôle de source de **changement.**<br />4. Cliquez **sur Unbind**.<br />5. Sélectionnez toutes les rangées.<br />6. Cliquez sur **Bind**.<br />7. Cliquez **sur OK** pour fermer la boîte de dialogue De contrôle de source **de changement.**<br />8. Acceptez la caisse si vous êtes invité.|La solution et le projet sont sous contrôle source.|
|Projet Rebind seulement sans fermer la boîte de dialogue **de changement source**|1. Créer un projet.<br />2. Ajouter uniquement le projet au contrôle des sources à l’aide (File->Source Control->Ajouter des projets sélectionnés au contrôle des sources.<br />3. Ouvrez la boîte de dialogue de contrôle de source de changement.<br />4. Non relis le projet.<br />5. Nier que le projet.|La solution reste incontrôlée.<br /><br /> Le projet reste contrôlé.|
|Solution rebinée seulement sans fermer la boîte de dialogue **de contrôle de source de changement**|1. Créer un projet.<br />2. Ajouter seulement la solution au contrôle de source à l’aide (**Fichier**, **Contrôle source**, Ajouter **des projets sélectionnés à la source de contrôle**.<br />3. Ouvrez la boîte de dialogue de contrôle de source de **changement.**<br />4. Non contraignant seulement la solution (Ne fermez pas la boîte de dialogue **de contrôle de source de changement.)**<br />5. N’attachez que la solution.<br />6. Cliquez **sur OK** pour fermer la boîte de dialogue.<br />7. Consultez les éléments de solution et de solution (le cas échéant.)|La solution reste contrôlée.<br /><br /> Le projet reste incontrôlé.|
|Solution/projet rebinée seulement lorsqu’il est dans le même répertoire|1. Créer un projet.<br />2. Ajouter seulement le projet au contrôle de source à l’aide (**Fichier**, **Contrôle source**, Ajouter **des projets sélectionnés à la source de contrôle**.<br />3. Fermez la solution.<br />4. Créer une nouvelle solution avec au moins deux projets.<br />5. Ajouter la solution au contrôle des sources.<br />6. Ajouter le projet créé dans l’étape 1 à partir du contrôle des sources.<br />7. Acceptez la caisse de la solution si elle est invitée.<br />8. Vérifiez toute la solution.<br />9. Ouvrez la boîte de dialogue de contrôle de source de **changement.**<br />10. Sélectionnez le projet ajouté (à partir de l’étape 6) et cliquez sur **Unbind**.<br />11. Cliquez **sur OK** pour fermer la boîte de dialogue.<br />12. Acceptez la caisse si vous êtes invité.<br />13. Réouverture de la boîte de dialogue **de contrôle des sources de** changement.<br />14. Sélectionnez le projet ajouté (à partir de l’étape 6) et cliquez sur **Bind**.<br />15. Sélectionnez l’emplacement d’origine.|La solution et les projets restent contrôlés.|

## <a name="see-also"></a>Voir aussi
- [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
