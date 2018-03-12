---
title: "Zone de test 3 : Check out-annuler l’extraction | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, checkout
- source control plug-ins, undo checkout
- source control [Visual Studio SDK], checking out
- source control [Visual Studio SDK], undo checkout
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8835f1f8c312b3aba72353625a1d97b514dc21b8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="test-area-3-check-outundo-checkout"></a>Zone de test 3 : Extraire / annuler l’extraction
Cette zone de plug-in de test de contrôle de code source traite les éléments de modification et de restauration à partir de la banque des versions via le **Check Out** et **annuler l’extraction** commandes.  
  
 **L’extraction**: marque un élément dans la banque des versions comme extrait, modifie la copie locale en lecture-écriture.  
  
 **Annuler l’extraction**: marque un élément dans la banque des versions archivé, rétablit la copie locale à l’état avant l’extraction (en fonction des options).  
  
## <a name="command-menu-access"></a>Accès au Menu de commande  
 Les éléments suivants [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] menu chemins d’environnement de développement intégré sont utilisés dans les cas de test.  
  
##### <a name="check-out"></a>Vérifier :  
  
-   **Fichier**, **contrôle de code Source**, **extraire**.  
  
-   **Fichier**, **extraire**.  
  
-   Menu contextuel, **extraire**.  
  
-   Annuler l’extraction : **fichier**, **contrôle de code Source**, **annuler l’extraction**.  
  
## <a name="common-expected-behavior"></a>Comportement attendu commun  
  
-   Après l’opération d’extraction, la cible ou les fichiers et/ou les dossiers sont marqués comme extraits dans la banque des versions.  
  
-   L’extraction d’attributs de la banque des versions à l’utilisateur approprié.  
  
-   La date et heure de l’extraction sont corrects (par les paramètres de l’utilisateur).  
  
## <a name="test-cases"></a>Cas de test  
 Voici les cas de test spécifiques pour la zone de test de l’extraction/annuler l’extraction.  
  
### <a name="case-3a-check-out"></a>Cas 3 : extraire  
 Cette section se concentre sur le fonctionnement de la commande d’extraction.  
  
|Action|Étapes de test|Résultats attendus à vérifier|  
|------------|----------------|--------------------------------|  
|Vérifiez les exclusif (commun) un projet client|1.  Créez un projet de client.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Extrayez l’ensemble du projet de manière exclusive (**fichier**, **Check Out**).|La modification se produit.|  
|Vérifiez en mode exclusif (commun), un système de fichiers ou d’un projet Web IIS local|1.  Définir la connexion au serveur Web dans le fichier de partage dans **outils**, **Options**, **projets**, **paramètres Web**.<br />2.  Créez un projet web.<br />3.  Ajouter la solution au contrôle de code source.<br />4.  Extrayez l’ensemble du projet de manière exclusive (**fichier**, **contrôle de code Source**, **Check Out**).|La modification se produit.|  
|Extraire des éléments de solution dans une solution (nouvelle méthode de gestion des autres fichiers)|1.  Créez une solution vide.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Extraire la solution.<br />4.  Ajouter plusieurs éléments de solution.<br />5.  Vérifiez tous les éléments qui vient d’être ajouté.<br />6.  Sélectionner plusieurs éléments de solution.<br />7.  Extraire les éléments sélectionnés (Menu contextuel, **Check Out**).|Fichiers sélectionnés ont été extraits.|  
|Extraire la Version locale (si le plug-in de test prend en charge cette fonctionnalité)|1.  Utilisateur 1 : Créer un projet client.<br />2.  L’utilisateur 1 : Ajouter la solution au contrôle de code source.<br />3.  L’utilisateur 2 : Ouvrez la solution à partir du contrôle de code source vers un autre emplacement.<br />4.  Utilisateur 2 : Vérification d’extraction d’un fichier.<br />5.  L’utilisateur 2 : Modifier le fichier.<br />6.  L’utilisateur 2 : Vérifiez dans le fichier.<br />7.  Utilisateur 1 : Extraire de la version locale du fichier (vérifier le **extraire la Version locale** option dans avancée **Check Out** boîte de dialogue).|La version locale du fichier est extrait.<br /><br /> Les modifications apportées par l’utilisateur 2 ne sont pas appliquées au fichier de l’utilisateur 1.|  
  
### <a name="case-3b-disconnected-check-out"></a>Cas 3 b : déconnecté d’extraction  
 Fonctionne en mode déconnecté permet aux utilisateurs un niveau de prise en charge du contrôle source continue lorsque ne pas connectées directement à une banque de versions. Pour cela, vous devez toutes les informations pertinentes sur la solution inscrite et les projets de mise en cache localement.  
  
 L’extraction exclusive des opérations peut se produire uniquement tout en étant connecté pour le magasin de contrôle de code source. Contrôle partagé des opérations peut se produire à tout moment, si connecté ou déconnecté. Par conséquent, quand vous êtes déconnecté de la banque des versions, uniquement le **vérifier partagé** (CO) commande est activée. Tout en étant déconnecté, **annuler l’extraction** est désactivée, car l’ancienne version ne peut pas être récupérée pour remplacer les modifications apportées par l’utilisateur.  
  
 Lorsque l’utilisateur se reconnecte à la version du magasin, les États de l’extraction de toutes les solutions inscrits et projets sont synchronisées. Cela ne les mises à jour nécessaires à la banque pour l’extraction de l’utilisateur a effectué. Une fois que la synchronisation s’est produit, l’utilisateur est en mesure de continuer à travailler comme d’habitude (connecté).  
  
#### <a name="expected-behavior"></a>Comportement attendu  
  
-   Impossible d’utiliser **Out exclusivement** commande tout en étant déconnecté de la banque des versions.  
  
-   Impossible d’utiliser **annuler l’extraction** commande tout en étant déconnecté de la banque des versions.  
  
-   **Partagé Check Out** commande fonctionne.  
  
|Action|Étapes de test|Résultats attendus à vérifier|  
|------------|----------------|--------------------------------|  
|Tout en étant déconnecté, extraire un fichier, puis vous connecter pour la synchronisation|1.  Déconnecter un projet contrôlé à l’aide de la boîte de dialogue Modifier le contrôle de code Source (**fichier**, **contrôle de code Source**, **contrôle de code Source modification**l).<br />2.  Extraire un fichier.<br />3.  Cliquez sur Extraire (déconnecté) dans la boîte de dialogue d’avertissement.<br />4.  Modifiez le fichier.<br />5.  Se connecter à l’aide de la boîte de dialogue Modifier le contrôle de code Source.<br />6.  Obtenir la dernière Version du fichier modifié.|Comportement attendu commun|  
  
### <a name="case-3c-query-editquery-save-qeqs"></a>Cas 3c : modifier la requête/requête enregistrer (QEQS)  
 Les éléments sous contrôle de code source sont suivis pour les modifications, les modifications, et enregistre pour aider les utilisateurs facilement gérer leurs fichiers. Lorsque vous modifiez un article contrôlé est « activé », QEQS intercepte la modification a été lancée et demande à l’utilisateur s’il souhaite extraire le fichier pour le modifier. En fonction de **outils**, **Options** paramètres, l’utilisateur est forcé à extraire le fichier afin de modifier ou peut être autorisés à modifier une copie en mémoire et extraire plus tard. Si l’utilisateur **outils**, **Options** paramètre n’est pas défini pour afficher la boîte de dialogue d’extraction et vérifier son évolution horizontale, alors que l’utilisateur effectue sa modification, le fichier extrait automatiquement, chaque fois que possible.  
  
#### <a name="expected-behavior"></a>Comportement attendu  
  
-   Après l’opération d’extraction, la cible ou les fichiers et/ou les dossiers sont marqués comme extraits dans la banque des versions.  
  
-   L’extraction d’attributs de la banque des versions à l’utilisateur approprié.  
  
-   La date et heure de l’extraction sont corrects (par les paramètres de l’utilisateur).  
  
-   La copie locale du fichier cible ou du dossier est accessible en écriture.  
  
|Action|Étapes de test|Résultats attendus à vérifier|  
|------------|----------------|--------------------------------|  
|Modifier le fichier texte est archivé|1.  Créez un projet contenant un fichier texte.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Définissez **outils**, **Options**, **contrôle de code Source**, **autoriser la modification pendant qu’en lecture seule sur le disque des fichiers** à désactivé.<br />4.  Définissez **outils**, **Options**, **contrôle de code Source**, **demander l’extraction** dans le **lorsque vous archivez les fichiers sont modifiés** zone de liste déroulante.<br />5.  Définissez **outils**, **Options**, **contrôle de code Source**, **demander l’extraction** dans le **lorsque vous archivez les fichiers sont enregistrés** zone de liste déroulante.<br />6.  Ouvrez le fichier texte dans l’éditeur, essayez de taper un nouveau texte dans le fichier. Si cette étape est exécutée correctement, passez à l’étape suivante.<br />7.  Cliquez sur **Annuler** dans les **extraire pour modification** boîte de dialogue. Si cette étape est exécutée correctement, passez à l’étape suivante.<br />8.  Définissez **outils**, **Options**, **contrôle de code Source**, **autoriser la modification pendant qu’en lecture seule sur le disque des fichiers** cochée.<br />9. Ouvrez le fichier projet dans l’éditeur, essayez de taper le nouveau texte dans le fichier. Si cette étape est exécutée correctement, passez à l’étape suivante.<br />10. Cliquez sur **modifier** dans les **extraire pour modification** boîte de dialogue. Si cette étape est exécutée correctement, passez à l’étape suivante.<br />11. Modifiez le fichier texte et tentez de l’enregistrer.|`Result of step 6:`<br /><br /> Extraire de la boîte de dialogue s’affiche.<br /><br /> `Result of step 7:`<br /><br /> Le fichier est identique.<br /><br /> `Result of step 9:`<br /><br /> Extraire de la boîte de dialogue s’affiche.<br /><br /> `Result of step 10:`<br /><br /> Vous pouvez modifier le fichier de projet en mémoire.<br /><br /> `Result of step 11:`<br /><br /> Sur Enregistrer, l’extraction sur la boîte de dialogue d’enregistrement apparaît.|  
|Modifier un fichier de solution qui est archivé|Répétez les étapes comme décrit dans le précédent testent, mais au lieu de modifier un fichier texte, modifiez la solution en modifiant les propriétés de la solution.|Identique à la série de tests précédente|  
|Modifier un fichier projet est archivé|Répétez les étapes comme décrit dans le précédent testent, mais au lieu de modifier un fichier texte, modifiez le projet en modifiant les propriétés du projet.|Identique au test précédent.|  
  
### <a name="case-3d-silent-check-out"></a>Case 3d : Extraction en mode silencieux  
 Cette vérification d’arrière-plan sous-zone des scénarios où la **Check Out** boîte de dialogue n’apparaît pas par l’utilisateur **outils**, **Options**, **des paramètres de contrôle de code Source** .  
  
#### <a name="expected-behavior"></a>Comportement attendu  
  
-   Après l’opération d’extraction, la cible ou les fichiers et/ou les dossiers sont marqués comme extraits dans la banque des versions.  
  
-   L’extraction d’attributs de la banque des versions à l’utilisateur approprié.  
  
-   La date et heure de l’extraction est correcte (par les paramètres de l’utilisateur).  
  
-   La copie locale du fichier cible ou du dossier est accessible en écriture.  
  
|Action|Étapes de test|Résultats attendus à vérifier|  
|------------|----------------|--------------------------------|  
|Extraction d’un fichier sans assistance|1.  Définissez **outils**, **Options**, **contrôle de code Source** à **extraire les fichiers automatiquement dans le menu Edition**.<br />2.  Créer un nouveau projet avec un fichier.<br />3.  Ajouter la solution au contrôle de code source.<br />4.  Extraire le fichier.|Fichier est extrait en mode silencieux (pas d’interface utilisateur).|  
|Extraction en mode silencieux pour un projet|1.  Définissez **outils**, **Options**, **contrôle de code Source** à **extraire les fichiers automatiquement dans le menu Edition**.<br />2.  Créer un nouveau projet.<br />3.  Ajouter la solution au contrôle de code source.<br />4.  Extraire le projet.|Fichier est extrait en mode silencieux (pas d’interface utilisateur).|  
  
### <a name="case-3e-undo-check-out"></a>Cas 3e : annuler l’extraction  
 **Annuler l’extraction** est utilisée pour annuler d’un fichier d’état d’extraction et d’éviter la vérification des modifications apportées au fichier.  
  
#### <a name="expected-behavior"></a>Comportement attendu  
  
-   La valeur par défaut est basé sur l’utilisateur **extraire la Version locale** paramètre. Si l’utilisateur a choisi d’extraire la version locale, la valeur par défaut pour annuler l’extraction est toujours revenir à la version extraite.  
  
-   Après la réception de l’annulation, les icônes de **l’Explorateur de solutions** sont mis à jour pour les fichiers et l’élément est supprimé de la **archivages en attente** fenêtre.  
  
|Action|Étapes de test|Résultats attendus à vérifier|  
|------------|----------------|--------------------------------|  
|Annuler l’extraction d’un fichier unique qui est extrait en mode exclusif|1.  Créez un projet de client.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Extraire un fichier exclusivement.<br />4.  Modifier le fichier.<br />5.  Annuler l’extraction (**fichier**, **contrôle de code Source**, **annuler l’extraction**).|Comportement attendu commun.|  
|Annuler l’extraction d’un fichier unique qui est extrait en mode partagé|1.  Créez un projet de client.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Extraire un fichier partagé.<br />4.  Modifier le fichier.<br />5.  Annuler l’extraction (**fichier**, **contrôle de code Source**, **annuler l’extraction**).|Comportement attendu commun.|  
|Annuler l’extraction d’un projet après l’ajout de fichiers au projet|1.  Créez un projet et l’ajouter au contrôle de code source.<br />2.  Extraire le projet.<br />3.  Ajoutez un fichier au projet.<br />4.  Annuler l’extraction du projet.|Fichier ajouté est supprimé du projet dans l’Explorateur de solutions.<br /><br /> Projet est n’est plus extrait.|  
|Annuler l’extraction d’un projet après la suppression des fichiers à partir du projet|1.  Créez un projet et l’ajouter au contrôle de code source.<br />2.  Extraire le projet.<br />3.  Supprimer un fichier à partir du projet.<br />4.  Annuler l’extraction du projet.|Fichier supprimé s’affiche sous le projet dans l’Explorateur de solutions.<br /><br /> Projet est n’est plus extrait.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)