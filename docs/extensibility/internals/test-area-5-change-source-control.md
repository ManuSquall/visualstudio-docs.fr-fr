---
title: 'Zone de test 5 : modifier le contrôle de code source | Microsoft Docs'
description: Cette zone de test du plug-in de contrôle de code source explique comment modifier le contrôle de code source à l’aide de la commande modifier le contrôle de code source.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 88dcc8e86da43f330c50ea478aaee572c1c3a060
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898133"
---
# <a name="test-area-5-change-source-control"></a>Zone de test 5 : Changer le contrôle de code source
Cette zone de test du plug-in de contrôle de code source couvre la modification du contrôle de code source via la commande **modifier le contrôle de code source** .

 La commande **modifier le contrôle de code source** fournit quatre fonctions de base pour l’utilisateur :

- **Établis**

   Permet à un utilisateur d’établir ou de rétablir un lien de contrôle de code source entre une solution/un projet et la Banque des versions.

- **Dissoci**

   Supprime un projet/une solution du contrôle de code source en fonction de la connexion.

- **Connexion/déconnexion :**

  Active/désactive l’état connecté ou hors connexion de la solution contrôlée, qui est couverte dans la zone 3. Pour plus d’informations, consultez [zone de test 3 : extraire/annuler l’extraction](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).

## <a name="command-menu-access"></a>Accès au menu commande
 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chemin d’accès au menu de l’environnement de développement intégré suivant est utilisé dans les cas de test.

 Modifier le contrôle de code source :**fichier**, **contrôle de code source**, **modifier le contrôle de code source**.

## <a name="test-cases"></a>Cas de test
 Les éléments suivants sont des cas de test spécifiques pour la zone de test de la commande **modifier le contrôle de code source** .

### <a name="case-5a-bind"></a>Cas 5A : lier
 La liaison permet à l’utilisateur d’ajouter des informations de contrôle de code source aux projets et solutions sélectionnés. En général, l’utilisateur est invité à identifier un projet dans le contrôle de code source auquel ils doivent être ajoutés. L’utilisateur ne peut pas créer un nouveau projet dans le contrôle de code source dans le cadre de cette opération (contrairement au contrôle ajouter au contrôle de code source).

| Action | Étapes de test | Résultats attendus à vérifier |
| - | - | - |
| Lier à l’emplacement vide | 1. Créez un projet.<br />2. Ajoutez la solution au contrôle de code source.<br />3. Ouvrez la boîte de dialogue **modifier le contrôle de code source** (**fichier**, **contrôle de code source**, **modifier le contrôle de code source**).<br />4. cliquez sur **annuler la liaison**.<br />5. accepter la boîte de dialogue d’avertissement si elle s’affiche.<br />6. Sélectionnez tous les éléments.<br />7. cliquez sur **lier**.<br />8. Accédez à un emplacement vide dans un magasin de contrôle de code source.<br />9. cliquez sur **OK** pour fermer la boîte de dialogue **modifier le contrôle de code source** .<br />10. cliquez sur **continuer avec ces liaisons** dans la boîte de dialogue de confirmation.<br />11. cliquez sur **OK** dans la boîte de dialogue d’avertissement si elle s’affiche.<br />12. tout archiver. Si cette étape se déroule correctement, passez à l’étape suivante.<br />13. Ouvrez la solution du contrôle de code source vers un nouvel emplacement. | `Result from Step 12:`<br /><br /> La solution et le projet sont liés et écrits dans la nouvelle cible de la Banque des versions.<br /><br /> Les fichiers solution et projet sont archivés.<br /><br /> La hiérarchie de projet de la Banque des versions correspond à la hiérarchie des dossiers du projet sur le disque.<br /><br /> `Result from Step 13:`<br /><br /> Tous les éléments de projet sont téléchargés. |
| Lier à l’emplacement synchronisé avec le client | 1. Créez un projet.<br />2. Ajoutez la solution au contrôle de code source.<br />3. Créez un doublon de la solution et du projet dans la Banque des versions (partager et créer une branche si vous utilisez [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ).<br />4. Ouvrez la boîte de dialogue **modifier le contrôle de code source** (**fichier**, **contrôle de code source**, **modifier le contrôle de code source**).<br />5. dissocier tout.<br />6. cliquez sur **OK** pour fermer la boîte de dialogue **modifier le contrôle de code source** .<br />7. rouvrez la boîte de dialogue **modifier le contrôle de code source** .<br />8. Sélectionnez tout.<br />9. cliquez sur **lier**.<br />10. Accédez à l’emplacement des branches de la solution et du projet (à partir de l’étape 3)<br />11. cliquez sur **OK** pour fermer la boîte de dialogue **modifier le contrôle de code source** .<br />12. obtenir la dernière version de manière récursive pour tous les éléments. | Le contenu d’un fichier après la récupération est le même qu’avant l’extraction. |
| Lier à l’emplacement qui n’est pas synchronisé avec le client | 1. Créez un projet.<br />2. Ajoutez la solution au contrôle de code source.<br />3. Créez un doublon de la solution et du projet dans la Banque des versions (partager et créer une branche si vous utilisez [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ).<br />4. modifiez les fichiers dans le projet avec branches dans la Banque des versions.<br />5. Ouvrez la boîte de dialogue **modifier le contrôle de code source** (**fichier**, **contrôle de code source**, **modifier le contrôle de code source**).<br />6. séparer tout.<br />7. cliquez sur **OK** pour fermer la boîte de dialogue **modifier le contrôle de code source** .<br />8. rouvrez la boîte de dialogue **modifier le contrôle de code source** .<br />9. Sélectionnez tout.<br />10. cliquez sur **lier**.<br />11. Accédez à l’emplacement des branches pour la solution et le projet.<br />12. cliquez sur **OK** pour fermer la boîte de dialogue **modifier le contrôle de code source** .<br />13. accepter la boîte de dialogue d’avertissement si elle s’affiche.<br />14. obtenir la dernière récursivité pour tous les éléments. | Les fichiers qui ont été modifiés à l’étape 4 sont également modifiés localement. |
| Lier la solution qui n’était jamais sous le contrôle de code source | 1. Créez un dossier vide dans le contrôle de code source.<br />2. Créez un projet client.<br />3. Ouvrez la boîte de dialogue **modifier le contrôle de code source** (**fichier**, **contrôle de code source**, **modifier le contrôle de code source**).<br />4. liez la solution à un emplacement vide dans le contrôle de code source.<br />5. cliquez sur **OK** pour fermer la boîte de dialogue **modifier le contrôle de code source** .<br />6. cliquez sur **continuer avec ces liaisons** dans la boîte de dialogue de confirmation.<br />7. cliquez sur **OK** dans la boîte de dialogue d’avertissement si elle s’affiche. | La solution est ajoutée au contrôle de code source.<br /><br /> La solution et le projet sont extraits. |
| Annuler la liaison | 1. Créez un projet.<br />2. Ajoutez la solution au contrôle de code source.<br />3. Ouvrez la boîte de dialogue Modifier le contrôle de code source.<br />4. séparer tout.<br />5. cliquez sur le bouton **OK** pour fermer la boîte de dialogue. Si cette étape se déroule correctement, passez à l’étape suivante.<br />6. rouvrez la boîte de dialogue **modifier le contrôle de code source** .<br />7. lier à un emplacement non lié.<br />8. cliquez sur **Annuler**. | `Result from Step 5:`<br /><br /> La solution n’est plus sous contrôle de code source<br /><br /> `Result from Step 8:`<br /><br /> La solution n’est toujours pas sous contrôle de code source. |

### <a name="case-5b-unbind"></a>Cas 5B : Unbind
 Unbind supprime les informations de contrôle de code source des projets et de leur solution. Les projets et la solution affectés sont basés sur une combinaison de sélection de l’utilisateur et sur la façon dont les éléments ont été ajoutés au contrôle de code source.

|Action|Étapes de test|Résultats attendus à vérifier|
|------------|----------------|--------------------------------|
|Dissocier la solution contenant un système de fichiers ou un projet Web IIS local et un projet client|1. Créez un système de fichiers ou un projet Web IIS local.<br />2. Ajoutez la solution au contrôle de code source.<br />3. Ajoutez un nouveau projet client à la solution.<br />4. acceptez l’extraction de la solution si vous y êtes invité.<br />5. Ouvrez la boîte de dialogue **modifier le contrôle de code source** .<br />6. cliquez sur **annuler la liaison**.<br />7. cliquez sur **OK** pour fermer la boîte de dialogue.<br />8. tentative d’extraction de la solution, du projet, des éléments de solution et des éléments de projet.|La solution et les projets ne sont pas sous contrôle de code source.<br /><br /> Les commandes de menu du contrôle de code source n’apparaissent pas.|
|Annuler la liaison|1. Créez un projet.<br />2. Ajoutez la solution au contrôle de code source.<br />3. Ouvrez la boîte de dialogue **modifier le contrôle de code source** .<br />4. cliquez sur **dissocier tout**.<br />5. cliquez sur **Annuler**.|La solution est sous contrôle de code source.|

### <a name="case-5c-rebind"></a>Cas 5C : relier
 La reliaison est simplement une combinaison de liaison et de liaison, c’est-à-dire le processus de reliaison d’un projet ou d’une solution précédemment sous contrôle de code source et qui a été détachée.

|Action|Étapes de test|Résultats attendus à vérifier|
|------------|----------------|--------------------------------|
|Relier la solution et les projets sans fermer la boîte de dialogue **modifier le contrôle de code source**|1. Créez un projet.<br />2. Ajoutez la solution au contrôle de code source.<br />3. Ouvrez la boîte de dialogue **modifier le contrôle de code source** .<br />4. cliquez sur **annuler la liaison**.<br />5. Sélectionnez toutes les lignes.<br />6. cliquez sur **lier**.<br />7. cliquez sur **OK** pour fermer la boîte de dialogue **modifier le contrôle de code source** .<br />8. acceptez l’extraction si vous y êtes invité.|La solution et le projet sont sous contrôle de code source.|
|Relier le projet uniquement sans fermer la boîte de dialogue **modifier le contrôle de code source**|1. Créez un projet.<br />2. Ajoutez uniquement le projet au contrôle de code source à l’aide de (contrôle de source de >de fichiers->ajouter les projets sélectionnés au contrôle de code source.<br />3. Ouvrez la boîte de dialogue Modifier le contrôle de code source.<br />4. dissociez uniquement le projet.<br />5. liez uniquement le projet.|La solution reste non contrôlée.<br /><br /> Le projet reste contrôlé.|
|Relier la solution uniquement sans fermer la boîte de dialogue **modifier le contrôle de code source**|1. Créez un projet.<br />2. Ajoutez uniquement la solution au contrôle de code source à l’aide de (**fichier**, **contrôle de code source**, **Ajoutez les projets sélectionnés au contrôle de code source**.<br />3. Ouvrez la boîte de dialogue **modifier le contrôle de code source** .<br />4. dissociez uniquement la solution (ne fermez pas la boîte de dialogue **modifier le contrôle de code source** .)<br />5. liez uniquement la solution.<br />6. cliquez sur **OK** pour fermer la boîte de dialogue.<br />7. consultez les éléments de solution et de solution (le cas échéant).|La solution reste contrôlée.<br /><br /> Le projet reste non contrôlé.|
|Relier la solution/le projet uniquement dans le même répertoire|1. Créez un projet.<br />2. Ajoutez uniquement le projet au contrôle de code source à l’aide de (**fichier**, **contrôle de code source**, **Ajoutez les projets sélectionnés au contrôle de code source**.<br />3. Fermez la solution.<br />4. Créez une nouvelle solution avec au moins deux projets.<br />5. Ajoutez la solution au contrôle de code source.<br />6. Ajoutez le projet créé à l’étape 1 à partir du contrôle de code source.<br />7. acceptez l’extraction de la solution si vous y êtes invité.<br />8. archivez l’ensemble de la solution.<br />9. Ouvrez la boîte de dialogue **modifier le contrôle de code source** .<br />10. Sélectionnez le projet ajouté (de l’étape 6), puis cliquez sur **annuler la liaison**.<br />11. cliquez sur **OK** pour fermer la boîte de dialogue.<br />12. acceptez l’extraction si vous y êtes invité.<br />13. rouvrez la boîte de dialogue **modifier le contrôle de code source** .<br />14. Sélectionnez le projet ajouté (de l’étape 6), puis cliquez sur **lier**.<br />15. Sélectionnez l’emplacement d’origine.|La solution et les projets restent contrôlés.|

## <a name="see-also"></a>Voir aussi
- [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
