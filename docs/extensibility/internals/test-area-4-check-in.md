---
title: "Zone de test 4&#160;: Archiver | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôle de code source (Visual Studio SDK), la vérification des éléments"
  - "contrôle plug-ins de source, archiver les éléments"
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Zone de test 4&#160;: Archiver
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cette zone de plug\-in de test de contrôle de code source couvre l’envoi d’éléments mis à jour dans la banque des versions via la **Archiver** commande.  
  
## Accès au Menu de commande  
 Les éléments suivants [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] menu chemins d’environnement de développement intégré sont utilisés dans les cas de test.  
  
##### Archiver :  
 **Fichier**, **contrôle de code Source**, **Archiver**.  
  
 **Fichier**, **Archiver**.  
  
 Menu contextuel, **Archiver**.  
  
## Comportement attendu commun  
  
-   Les projets et les fichiers ajoutés à une solution ou un projet sous contrôle de code source apparaissent dans le **Archiver** boîte de dialogue et les **Archivages en attente** fenêtre.  
  
-   Après l’archivage, les éléments ajoutés apparaissent dans le contrôle de code source.  
  
-   Après l’archivage, les éléments mis à jour sont correctement gérées dans le magasin.  
  
## Cas de test  
 Voici les cas de test spécifiques pour la zone de test d’intégration.  
  
### Cas 4 : modification des éléments  
 Décrit l’utilisation de la vérification en action pour mettre à jour un fichier sous contrôle de code source qui a été modifié.  
  
|Action|Étapes de test|Résultats attendus à vérifier|  
|------------|--------------------|-----------------------------------|  
|Modifier un fichier texte qui a été extrait, l’archivage de fichiers uniquement \(**Archiver** boîte de dialogue\)|1.  Créez un nouveau projet avec un fichier texte.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Extraire et modifier le fichier texte.<br />4.  Archivez via la boîte de dialogue Archiver \(**fichier**, **contrôle de code Source**, **Archiver**\).|Comportement attendu commun.|  
|Modifier un fichier texte qui a été extrait, l’archivage de fichiers uniquement \(**Archivages en attente** fenêtre\)|1.  Créez un nouveau projet avec un fichier texte.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Extraire et modifier le fichier texte.<br />4.  Archivez la **Archivages en attente** fenêtre.|Comportement attendu commun.|  
  
### Cas 4 b : ajout de fichiers  
 Lorsque vous ajoutez un fichier à un projet ou un élément à une solution, le projet ou la solution doive changer également. Par conséquent, le fichier parent est également extrait et doit être archivé pour terminer l’ajout.  
  
|Action|Étapes de test|Résultats attendus à vérifier|  
|------------|--------------------|-----------------------------------|  
|Ajoutez un fichier texte et tout archiver \(**Archiver** boîte de dialogue\)|1.  Créer un nouveau projet.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Ajoutez un fichier texte au projet.<br />4.  Accepter l’extraction du projet si vous y êtes invité.<br />5.  Sélectionnez la solution dans **l’Explorateur de solutions**.<br />6.  Archiver depuis le **Archiver** boîte de dialogue.|Comportement attendu commun.|  
|Ajoutez un fichier texte et tout archiver \(**Archivages en attente** fenêtre\)|1.  Créer un nouveau projet.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Ajoutez un fichier texte au projet.<br />4.  Accepter l’extraction du projet si vous y êtes invité.<br />5.  Archiver la solution à partir de **Archivages en attente** fenêtre.|Comportement attendu commun|  
  
### Cas c 4 : ajout de projets  
 Lorsque vous ajoutez un projet à une solution, la solution doive changer également. Par conséquent, le fichier solution est également extrait et doit être archivé pour terminer l’ajout.  
  
|Action|Étapes de test|Résultats attendus à vérifier|  
|------------|--------------------|-----------------------------------|  
|Ajouter un projet à une solution sous contrôle de code source vide \(**Archiver** boîte de dialogue\)|1.  Créer une solution vide.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Ajouter un nouveau projet.<br />4.  Accepter l’extraction de la solution si vous y êtes invité.<br />5.  Archiver depuis le **Archiver** boîte de dialogue.|Comportement attendu commun.|  
|Ajouter un projet à une solution sous contrôle de code source vide \(**Archivages en attente** fenêtre\)|1.  Créer une solution vide.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Ajouter un nouveau projet.<br />4.  Accepter l’extraction de la solution si vous y êtes invité.<br />5.  Archiver la solution à partir de **Archivages en attente** fenêtre.|Comportement attendu commun.|  
  
## Voir aussi  
 [Guide d'évaluation pour les Plug\-ins de contrôle de code Source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)