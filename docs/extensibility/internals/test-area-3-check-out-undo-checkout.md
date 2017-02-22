---
title: "Zone de test 3&#160;: V&#233;rification out-annuler l’extraction | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "plug-ins de contrôle de code source, l’extraction"
  - "plug-ins de contrôle de source, annuler l’extraction"
  - "contrôle de code source (Visual Studio SDK), la récupération"
  - "extraction (Visual Studio SDK), contrôle de la source"
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Zone de test 3&#160;: Extraire / annuler l’extraction
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cette zone de plug\-in de test de contrôle de code source traite les éléments de modification et de restauration à partir de la banque des versions via la **Check Out** et **Annuler l’extraction** commandes.  
  
 **Check Out**: marque un élément dans la banque des versions comme extrait, modifie la copie locale en lecture\-écriture.  
  
 **Annuler l’extraction**: marque un élément dans la banque des versions archivé, rétablit la copie locale à l’état avant l’extraction \(en fonction des options\).  
  
## Accès au Menu de commande  
 Les éléments suivants [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] menu chemins d’environnement de développement intégré sont utilisés dans les cas de test.  
  
##### Extraire :  
  
-   **Fichier**, **contrôle de code Source**, **extraire**.  
  
-   **Fichier**, **extraire**.  
  
-   Menu contextuel, **extraire**.  
  
-   Annuler l’extraction : **fichier**, **contrôle de code Source**, **Annuler l’extraction**.  
  
## Comportement attendu commun  
  
-   Après l’opération d’extraction, l’ou les fichiers cibles et\/ou les dossiers sont marqués comme étant extrait dans la banque des versions.  
  
-   La banque des versions l’extraction des attributs à l’utilisateur approprié.  
  
-   La date et heure de l’extraction sont corrects \(par les paramètres de l’utilisateur\).  
  
## Cas de test  
 Voici les cas de test spécifiques pour la zone de test de validation\/annuler l’extraction.  
  
### Cas 3 : extraction  
 Cette section se concentre sur le fonctionnement de la commande d’extraction.  
  
|Action|Étapes de test|Résultats attendus à vérifier|  
|------------|--------------------|-----------------------------------|  
|Vérifiez les exclusif commun un projet client|1.  Créer un projet client.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Découvrez l’ensemble du projet exclusivement \(**fichier**, **Check Out**\).|Extraction se produit.|  
|Vérifiez en mode exclusif \(commun\), un système de fichiers ou un projet Web IIS local|1.  Définir la connexion au serveur Web dans le fichier de partage dans **outils**, **Options**, **projets**, **paramètres Web**.<br />2.  Créez un projet Web.<br />3.  Ajouter la solution au contrôle de code source.<br />4.  Découvrez l’ensemble du projet exclusivement \(**fichier**, **contrôle de code Source**, **Check Out**\).|Extraction se produit.|  
|Vérifiez les éléments de solution dans une solution \(nouvelle méthode pour la gestion des autres fichiers\)|1.  Créer une solution vide.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Découvrez la solution.<br />4.  Ajouter plusieurs éléments de solution.<br />5.  Vérifiez tous les éléments ajoutés.<br />6.  Sélectionner plusieurs éléments de solution.<br />7.  Extraire les éléments sélectionnés \(Menu contextuel, **Check Out**\).|Fichiers sélectionnés ont été extraits.|  
|Extraire la Version locale \(si le plug\-in de test prend en charge cette fonctionnalité\)|1.  L’utilisateur 1 : Créer un projet client.<br />2.  L’utilisateur 1 : Ajouter la solution au contrôle de code source.<br />3.  L’utilisateur 2 : Ouvrez la solution de contrôle de code source vers un autre emplacement.<br />4.  L’utilisateur 2 : Extraire un fichier.<br />5.  L’utilisateur 2 : Modifier le fichier.<br />6.  L’utilisateur 2 : Vérifier dans le fichier.<br />7.  Utilisateur 1 : Extraire une version locale du fichier \(vérifier le **extraire la Version locale** option dans avancée **Check Out** boîte de dialogue\).|La version locale du fichier est extrait.<br /><br /> Modifications apportées par l’utilisateur 2 ne sont pas appliquées au fichier de l’utilisateur 1.|  
  
### Cas 3 b : déconnecté d’extraction  
 Fonctionne en mode hors connexion permet aux utilisateurs un niveau de prise en charge du contrôle source continue lorsque ne pas relié directement à un magasin de version. Pour cela, vous devez toutes les informations pertinentes sur les projets et solutions inscrite de mise en cache localement.  
  
 L’extraction exclusive des opérations peut se produire uniquement lorsque vous êtes connecté à la banque de contrôle source. Contrôle partagé des opérations peut se produire à tout moment, si connecté ou déconnecté. Par conséquent, quand vous êtes déconnecté de la banque des versions, uniquement les **Vérifier partagé** \(CO\) commande est activée. Lors de la déconnexion, **Annuler l’extraction** est désactivée, car l’ancienne version ne peut pas être récupérée pour remplacer les modifications apportées par l’utilisateur.  
  
 Lorsque l’utilisateur se reconnecte à la version stocker, les États de validation de toutes les solutions inscrites et projets sont synchronisées. Cela effectue les mises à jour nécessaires au magasin pour que l’utilisateur a effectué l’extraction. Une fois que la synchronisation s’est produit, l’utilisateur est en mesure de continuer à travailler comme d’habitude \(connecté\).  
  
#### Comportement attendu  
  
-   Impossible d’utiliser **Out exclusivement** commande lors de la déconnexion de la banque des versions.  
  
-   Impossible d’utiliser **Annuler l’extraction** commande lors de la déconnexion de la banque des versions.  
  
-   **Partagé Check Out** commande fonctionne.  
  
|Action|Étapes de test|Résultats attendus à vérifier|  
|------------|--------------------|-----------------------------------|  
|Lors de la déconnexion, extraire un fichier, puis connectez\-vous pour la synchronisation|1.  Déconnecter un projet contrôlé à l’aide de la boîte de dialogue Modifier le contrôle de code Source \(**fichier**, **contrôle de code Source**, **contrôle de code Source modification**l\).<br />2.  Extraire un fichier.<br />3.  Cliquez sur Extraire \(déconnecté\) dans la boîte de dialogue d’avertissement.<br />4.  Modifiez le fichier.<br />5.  Connectez\-vous à l’aide de la boîte de dialogue Modifier le contrôle de code Source.<br />6.  Obtenir la dernière Version du fichier modifié.|Comportement attendu commun|  
  
### Cas 3c : modifier la requête\/requête enregistrer \(QEQS\)  
 Éléments sous contrôle de code source sont suivis pour les modifications, les modifications, et l’enregistre pour permettre aux utilisateurs de facilement gérer leurs fichiers. Lorsque vous modifiez un article contrôlé est « activé », QEQS intercepte la modification a été lancée et demande à l’utilisateur s’il souhaite extraire le fichier pour le modifier. En fonction de **outils**, **Options** paramètres, l’utilisateur est forcé à extraire le fichier pour pouvoir modifier ou peut être autorisés à modifier une copie en mémoire et extraire ultérieurement. Si l’utilisateur **outils**, **Options** paramètre n’est pas défini pour afficher la boîte de dialogue d’extraction et simplement extrayez\-le, puis que l’utilisateur effectue sa modification, le fichier extrait automatiquement, si possible.  
  
#### Comportement attendu  
  
-   Après l’opération d’extraction, l’ou les fichiers cibles et\/ou les dossiers sont marqués comme étant extrait dans la banque des versions.  
  
-   La banque des versions l’extraction des attributs à l’utilisateur approprié.  
  
-   La date et heure de l’extraction sont corrects \(par les paramètres de l’utilisateur\).  
  
-   La copie locale du fichier cible ou du dossier est accessible en écriture.  
  
|Action|Étapes de test|Résultats attendus à vérifier|  
|------------|--------------------|-----------------------------------|  
|Modifier le fichier texte est archivé|1.  Créez un projet contenant un fichier texte.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Définissez **outils**, **Options**, **contrôle de code Source**, **Autoriser la modification pendant qu’en lecture seule sur le disque des fichiers** à désactivé.<br />4.  Définissez **outils**, **Options**, **contrôle de code Source**, **invite pour l’extraction** dans les **lorsque vous archivez les fichiers sont modifiés** zone de liste déroulante.<br />5.  Définissez **outils**, **Options**, **contrôle de code Source**, **invite pour l’extraction** dans les **lorsque vous archivez les fichiers sont enregistrés** zone de liste déroulante.<br />6.  Ouvrez le fichier texte dans l’éditeur, essayez de taper le nouveau texte dans le fichier. Si cette étape réussit, passez à l’étape suivante.<br />7.  Cliquez sur **Annuler** dans les **Extraire pour modification** boîte de dialogue. Si cette étape réussit, passez à l’étape suivante.<br />8.  Définissez **outils**, **Options**, **contrôle de code Source**, **Autoriser la modification pendant qu’en lecture seule sur le disque des fichiers** cochée.<br />9. Ouvrez le fichier de projet dans l’éditeur, essayez de taper le nouveau texte dans le fichier. Si cette étape réussit, passez à l’étape suivante.<br />10. Cliquez sur **Modifier** dans les **Extraire pour modification** boîte de dialogue. Si cette étape réussit, passez à l’étape suivante.<br />11. Modifiez le fichier texte et tentez de l’enregistrer.|`Result of step 6:`<br /><br /> Extraire de la boîte de dialogue s’affiche.<br /><br /> `Result of step 7:`<br /><br /> Le fichier reste inchangé.<br /><br /> `Result of step 9:`<br /><br /> Extraire de la boîte de dialogue s’affiche.<br /><br /> `Result of step 10:`<br /><br /> Vous pouvez modifier le fichier de projet en mémoire.<br /><br /> `Result of step 11:`<br /><br /> Enregistrer l’extraction sur boîte de dialogue d’enregistrement apparaît.|  
|Modifier un fichier de solution est archivé|Répétez les étapes comme décrit dans la précédente de test, mais au lieu de modifier un fichier texte, modifiez la solution en modifiant les propriétés de la solution.|Identique à la série de tests précédente|  
|Modifier un fichier de projet est archivé|Répétez les étapes comme décrit dans la précédente de test, mais au lieu de modifier un fichier texte, modifiez le projet en modifiant les propriétés du projet.|Identique au test précédent.|  
  
### Case 3d : Extraction en mode silencieux  
 Cette vérification d’arrière\-plan sous\-zone des scénarios où les **Check Out** boîte de dialogue n’apparaît pas par l’utilisateur **outils**, **Options**, **les paramètres de contrôle de code Source**.  
  
#### Comportement attendu  
  
-   Après l’opération d’extraction, l’ou les fichiers cibles et\/ou les dossiers sont marqués comme étant extrait dans la banque des versions.  
  
-   La banque des versions l’extraction des attributs à l’utilisateur approprié.  
  
-   La date et heure de l’extraction est correcte \(par les paramètres de l’utilisateur\).  
  
-   La copie locale du fichier cible ou du dossier est accessible en écriture.  
  
|Action|Étapes de test|Résultats attendus à vérifier|  
|------------|--------------------|-----------------------------------|  
|Extraction en mode silencieux pour un fichier|1.  Définissez **outils**, **Options**, **contrôle de code Source** à **fichiers extraction automatiquement sur Modifier**.<br />2.  Créer un nouveau projet avec un fichier.<br />3.  Ajouter la solution au contrôle de code source.<br />4.  Extraire le fichier.|Fichier est extrait en mode silencieux \(sans interface utilisateur\).|  
|Extraction en mode silencieux pour un projet|1.  Définissez **outils**, **Options**, **contrôle de code Source** à **fichiers extraction automatiquement sur Modifier**.<br />2.  Créer un nouveau projet.<br />3.  Ajouter la solution au contrôle de code source.<br />4.  Extraire le projet.|Fichier est extrait en mode silencieux \(sans interface utilisateur\).|  
  
### Cas 3e : annuler l’extraction  
 **Annuler l’extraction** est utilisé pour l’annulation d’un fichier d’état d’extraction et d’éviter d’archiver les modifications apportées au fichier.  
  
#### Comportement attendu  
  
-   La valeur par défaut est basé sur l’utilisateur **extraire la Version locale** paramètre. Si l’utilisateur a choisi d’extraire la version locale, la valeur par défaut pour annuler l’extraction est toujours revenir à la version extraite.  
  
-   Après la réception de l’annulation, les icônes de **l’Explorateur de solutions** sont mises à jour d’affectée fichiers et l’élément est supprimé de la **Archivages en attente** fenêtre.  
  
|Action|Étapes de test|Résultats attendus à vérifier|  
|------------|--------------------|-----------------------------------|  
|Annuler l’extraction d’un fichier unique qui est extrait en mode exclusif|1.  Créer un projet client.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Extraire un fichier exclusivement.<br />4.  Modifier le fichier.<br />5.  Annuler l’extraction \(**fichier**, **contrôle de code Source**, **Annuler l’extraction**\).|Comportement attendu commun.|  
|Annuler l’extraction d’un fichier unique qui est extrait en mode partagé|1.  Créer un projet client.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Extraire un fichier partagé.<br />4.  Modifier le fichier.<br />5.  Annuler l’extraction \(**fichier**, **contrôle de code Source**, **Annuler l’extraction**\).|Comportement attendu commun.|  
|Annuler l’extraction d’un projet après l’ajout de fichiers au projet|1.  Créez un nouveau projet et l’ajouter au contrôle de code source.<br />2.  Extraire le projet.<br />3.  Ajoutez un fichier au projet.<br />4.  Annuler l’extraction du projet.|Fichier ajouté est supprimé du projet dans l’Explorateur de solutions.<br /><br /> Projet n’est pas extrait.|  
|Annuler l’extraction d’un projet après la suppression de fichiers à partir du projet|1.  Créez un nouveau projet et l’ajouter au contrôle de code source.<br />2.  Extraire le projet.<br />3.  Supprimer un fichier du projet.<br />4.  Annuler l’extraction du projet.|Fichier supprimé s’affiche sous le projet dans l’Explorateur de solutions.<br /><br /> Projet n’est pas extrait.|  
  
## Voir aussi  
 [Guide d'évaluation pour les Plug\-ins de contrôle de code Source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)