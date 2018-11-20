---
title: 'Zone de test 5 : Modifier le contrôle de code Source | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d117d3ad85d46bfeeb896892508ba90efb33e702
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51746601"
---
# <a name="test-area-5-change-source-control"></a>Zone de test 5 : Modifier le contrôle de code source
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cette zone de test plug-in de contrôle de code source couvre la modification du contrôle de code source via le **modifier le contrôle de Source** commande.  
  
 **Modifier le contrôle de code Source** commande fournit quatre fonctions de base pour l’utilisateur :  
  
- **Lier :**  
  
   Permet à un utilisateur de définir ou de rétablir un lien de contrôle de source entre une solution/projet et de la banque des versions.  
  
- **Annuler la liaison :**  
  
   Supprime une projet/solution de contrôle de code source sur une base par connexion.  
  
- **Connecter/déconnecter :**  
  
  Active ou désactive les état connecté ou hors connexion de la solution contrôlée, qui est présentée dans la zone 3. Pour plus d’informations, consultez [Test zone 3 : extraire / annuler l’extraction](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).  
  
## <a name="command-menu-access"></a>Accès au Menu de commande  
 Ce qui suit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] chemin de menu environnement de développement intégré est utilisé dans les cas de test.  
  
 Modification de contrôle de code Source :**fichier**, **contrôle de code Source**, **modifier le contrôle de code Source**.  
  
## <a name="test-cases"></a>Cas de test  
 Les éléments suivants sont des cas de test spécifiques pour le **modifier le contrôle de Source** commande zone de test.  
  
### <a name="case-5a-bind"></a>Cas 5 a : lier  
 Liaison permet à l’utilisateur Ajouter des informations de contrôle de code source pour les projets sélectionnés et les solutions. L’utilisateur est généralement invité à identifier un projet dans le contrôle de code source à laquelle ils doivent être ajoutées. L’utilisateur ne peut pas créer un nouveau projet dans le contrôle de code source dans le cadre de cette opération (contraste avec les ajouter au contrôle de code Source).  
  
|Action|Étapes de test|Résultats attendus pour vérifier|  
|------------|----------------|--------------------------------|  
|Lier à un emplacement vide|1.  Créez un projet.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Ouvrez **modifier le contrôle de Source** boîte de dialogue (**fichier**, **contrôle de code Source**, **modifier le contrôle de Source**).<br />4.  Cliquez sur **Unbind**.<br />5.  Accepter la boîte de dialogue d’avertissement s’il apparaît.<br />6.  Sélectionnez tous les éléments.<br />7.  Cliquez sur **lier**.<br />8.  Accédez à un emplacement vide dans un magasin de contrôle de code source.<br />9. Cliquez sur **OK** pour fermer la **modifier le contrôle de Source** boîte de dialogue.<br />10. Cliquez sur **continuer avec ces liaisons** dans la boîte de dialogue de confirmation.<br />11. Cliquez sur **OK** dans la boîte de dialogue d’avertissement s’il apparaît.<br />12. Tout archiver. Si cette étape réussit, passez à l’étape suivante.<br />13. Ouvrez la solution à partir du contrôle de code source vers un nouvel emplacement.|`Result from Step 12:`<br /><br /> Solution projet lié à et sont écrits dans la nouvelle cible dans la banque des versions.<br /><br /> Fichiers solution et projet sont archivés.<br /><br /> Hiérarchie de projet du magasin de version correspond à l’arborescence des dossiers du projet sur le disque.<br /><br /> `Result from Step 13:`<br /><br /> Tous les éléments de projet sont téléchargés.|  
|Lier à un emplacement qui est synchronisée avec le client|1.  Créez un projet.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Créer un doublon de la solution et le projet dans la banque des versions (partager et créer une branche si vous utilisez [!INCLUDE[vsvss](../../includes/vsvss-md.md)]).<br />4.  Ouvrez **modifier le contrôle de Source** boîte de dialogue (**fichier**, **contrôle de code Source**, **modifier le contrôle de Source**).<br />5.  Tout dissocier.<br />6.  Cliquez sur **OK** pour fermer **modifier le contrôle de Source** boîte de dialogue.<br />7.  Rouvrez **modifier le contrôle de Source** boîte de dialogue.<br />8.  Sélectionner tout.<br />9. Cliquez sur **lier**.<br />10. Accédez à l’emplacement qui possèdent des branches de la solution et le projet (à l’étape 3)<br />11. Cliquez sur **OK** pour fermer la **modifier le contrôle de Source** boîte de dialogue.<br />12. Obtenir la dernière de manière récursive pour tous les éléments.|Contenu du fichier une fois que la méthode get est le même qu’avant la méthode get.|  
|Lier à un emplacement qui est synchronisée avec le client|1.  Créez un projet.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Créer un doublon de la solution et le projet dans la banque des versions (partager et créer une branche si vous utilisez [!INCLUDE[vsvss](../../includes/vsvss-md.md)]).<br />4.  Modifier les fichiers dans le projet avec des branches dans la banque des versions.<br />5.  Ouvrez **modifier le contrôle de Source** boîte de dialogue (**fichier**, **contrôle de code Source**, **modifier le contrôle de Source**).<br />6.  Tout dissocier.<br />7.  Cliquez sur **OK** pour fermer **modifier le contrôle de Source** boîte de dialogue.<br />8.  Rouvrez **modifier le contrôle de Source** boîte de dialogue.<br />9. Sélectionner tout.<br />10. Cliquez sur **lier**.<br />11. Accédez à l’emplacement pour la solution et projet de branches.<br />12. Cliquez sur **OK** pour fermer la **modifier le contrôle de Source** boîte de dialogue.<br />13. Accepter la boîte de dialogue d’avertissement s’il apparaît.<br />14. Obtenir les dernières récursive pour tous les éléments.|Fichiers qui ont été modifiés à l’étape 4 sont également modifiés localement.|  
|Solution de liaison qui n’était jamais sous contrôle de code source|1.  Créez un dossier vide dans le contrôle de code source.<br />2.  Créez un projet client.<br />3.  Ouvrez **modifier le contrôle de Source** boîte de dialogue (**fichier**, **contrôle de code Source**, **modifier le contrôle de Source**).<br />4.  Lier la solution à un emplacement vide dans le contrôle de code source.<br />5.  Cliquez sur **OK** pour fermer la **modifier le contrôle de Source** boîte de dialogue.<br />6.  Cliquez sur **continuer avec ces liaisons** dans la boîte de dialogue de confirmation.<br />7.  Cliquez sur **OK** dans la boîte de dialogue d’avertissement s’il apparaît.|Solution est ajoutée au contrôle de code source.<br /><br /> Solution et projet ont été extraits.|  
|Annuler la liaison|1.  Créez un projet.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Ouvrez la boîte de dialogue Modifier le contrôle de code Source.<br />4.  Tout dissocier.<br />5.  Cliquez sur **OK** bouton pour fermer la boîte de dialogue. Si cette étape réussit, passez à l’étape suivante.<br />6.  Rouvrez le **modifier le contrôle de Source** boîte de dialogue.<br />7.  Lier à un emplacement non liée.<br />8.  Cliquez sur **Annuler**.|`Result from Step 5:`<br /><br /> La solution n’est plus sous contrôle de code source<br /><br /> `Result from Step 8:`<br /><br /> Solution est toujours pas sous contrôle de code source.|  
  
### <a name="case-5b-unbind"></a>Cas 5 b : supprimer la liaison  
 La suppression supprime info de contrôle du code source à partir de projets et leurs solutions. La solution et projets affectés sont basées sur un mélange de sélection de l’utilisateur et comment les éléments ont été ajoutés au contrôle de code source.  
  
|Action|Étapes de test|Résultats attendus pour vérifier|  
|------------|----------------|--------------------------------|  
|Annuler la liaison de solution contenant un système de fichiers ou de projet Web IIS local et de projet d’un client|1.  Créez un système de fichiers ou d’un projet Web IIS local.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Ajouter un nouveau projet de client à la solution.<br />4.  Si vous y êtes invité, acceptez vérifier Out de la solution.<br />5.  Ouvrez le **modifier le contrôle de Source** boîte de dialogue.<br />6.  Cliquez sur **Unbind**.<br />7.  Cliquez sur **OK** pour fermer la boîte de dialogue.<br />8.  Tentative d’extraction de la solution, projet, éléments de solution, éléments de projet.|Solutions et projets ne sont pas sous contrôle de code source.<br /><br /> Commandes de menu de contrôle de code source n’apparaissent pas.|  
|Annuler la liaison de l’annulation|1.  Créez un projet.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Ouvrez le **modifier le contrôle de Source** boîte de dialogue.<br />4.  Cliquez sur **tout dissocier**.<br />5.  Cliquez sur **Annuler**.|Solution est sous contrôle de code source.|  
  
### <a name="case-5c-rebind"></a>Cas 5c : relier  
 La reliaison est simplement une combinaison de séparer et de liaison, le processus de projet/solution qui a été précédemment sous contrôle de code source et a été séparé de reliaison.  
  
|Action|Étapes de test|Résultats attendus pour vérifier|  
|------------|----------------|--------------------------------|  
|Relier des solutions et projets sans fermer la **modifier le contrôle de Source** boîte de dialogue|1.  Créez un projet.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Ouvrez le **modifier le contrôle de Source** boîte de dialogue.<br />4.  Cliquez sur **Unbind**.<br />5.  Sélectionnez toutes les lignes.<br />6.  Cliquez sur **lier**.<br />7.  Cliquez sur **OK** pour fermer la **modifier le contrôle de Source** boîte de dialogue.<br />8.  Si vous y êtes invité, acceptez l’extraction.|Solution et projet sont sous contrôle de code source.|  
|Lier de nouveau projet uniquement sans fermer **modifier le contrôle de Source** boîte de dialogue|1.  Créez un projet.<br />2.  Ajouter uniquement le projet au contrôle de code source à l’aide (fichier -> Source contrôle -> ajouter les projets sélectionnés au contrôle de code Source.<br />3.  Ouvrez la boîte de dialogue Modifier le contrôle de code Source.<br />4.  Annuler la liaison que le projet.<br />5.  Lier uniquement le projet.|Solution reste non contrôlée.<br /><br /> Projet reste contrôlée.|  
|Relier la solution uniquement sans fermer **modifier le contrôle de Source** boîte de dialogue|1.  Créez un projet.<br />2.  Ajouter uniquement la solution au contrôle de code source à l’aide (**fichier**, **contrôle de code Source**, **ajouter les projets sélectionnés au contrôle de code Source**.<br />3.  Ouvrez le **modifier le contrôle de Source** boîte de dialogue.<br />4.  Annuler la liaison uniquement la solution (ne fermez pas **modifier le contrôle de Source** boîte de dialogue.)<br />5.  Lier uniquement la solution.<br />6.  Cliquez sur **OK** pour fermer la boîte de dialogue.<br />7.  Découvrez des solutions et des éléments de solution (le cas échéant)|Solution reste contrôlée.<br /><br /> Projet reste non contrôlé.|  
|Relier la solution/projet uniquement dans même répertoire|1.  Créez un projet.<br />2.  Ajouter uniquement le projet au contrôle de code source à l’aide (**fichier**, **contrôle de code Source**, **ajouter les projets sélectionnés au contrôle de code Source**.<br />3.  Fermez la solution.<br />4.  Créer une solution avec au moins deux projets.<br />5.  Ajouter la solution au contrôle de code source.<br />6.  Ajoutez le projet créé à l’étape 1 à partir du contrôle de code source.<br />7.  Accepter l’extraction de la solution si vous y êtes invité.<br />8.  Archiver la solution entière.<br />9. Ouvrez le **modifier le contrôle de Source** boîte de dialogue.<br />10. Sélectionnez le projet ajouté (à partir de l’étape 6) et cliquez sur **Unbind**.<br />11. Cliquez sur **OK** pour fermer la boîte de dialogue.<br />12. Accepter l’extraction si vous y êtes invité.<br />13. Rouvrez **modifier le contrôle de Source** boîte de dialogue.<br />14. Sélectionnez le projet ajouté (à partir de l’étape 6) et cliquez sur **lier**.<br />15. Sélectionnez l’emplacement d’origine.|Solution et les projets restent contrôlées.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

