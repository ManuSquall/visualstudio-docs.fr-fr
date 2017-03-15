---
title: "How to: Add, Update, or Remove a WCF Data Service Reference | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "service references [Visual Studio]"
  - "WCF Data Service reference"
  - "WCF data service references"
  - "ADO.NET service references"
  - "ADO.NET Data Service reference"
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Add, Update, or Remove a WCF Data Service Reference
Une *référence de service* permet à un projet d'accéder à un ou plusieurs [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)].  Utilisez la boîte de dialogue **Ajouter une référence de service** pour rechercher [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] dans la solution actuelle, localement, sur un réseau local ou sur Internet.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Ajout d'une référence de service  
  
#### Pour ajouter une référence à un service externe  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le nom du projet auquel vous souhaitez ajouter le service, puis cliquez sur **Ajouter une référence de service**.  
  
     La boîte de dialogue **Ajouter une référence de service** s'affiche.  
  
2.  Dans la zone **Adresse**, entrez l'URL du service, puis cliquez sur **Aller à** pour rechercher le service.  Si le service implémente la sécurité du nom d'utilisateur et du mot de passe, vous serez peut\-être invité à entrer un nom d'utilisateur et un mot de passe.  
  
    > [!NOTE]
    >  Vous devez uniquement référencer des services provenant d'une source fiable.  Si vous ajoutez des références provenant d'une source non fiable, cela risque de compromettre la sécurité.  
  
     Vous pouvez sélectionner également l'URL dans la liste d'**adresses**, qui stocke les 15 URL précédentes pour lesquelles des métadonnées de service valides ont été trouvées.  
  
     Une barre de progression s'affiche pendant la recherche.  Vous pouvez arrêter à tout moment la recherche en cliquant sur **Arrêter**.  
  
3.  Dans la liste **Services**, développez le nœud du service que vous souhaitez utiliser et sélectionnez un jeu d'entités.  
  
4.  Dans la zone **Espace de noms**, entrez l'espace de noms que vous souhaitez utiliser pour la référence.  
  
5.  Cliquez sur **OK** pour ajouter la référence au projet.  
  
     Un client de service \(proxy\) est généré et les métadonnées qui décrivent le service sont ajoutées au fichier app.config.  
  
#### Pour ajouter une référence à un service dans la solution actuelle  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le nom du projet auquel vous souhaitez ajouter le service, puis cliquez sur **Ajouter une référence de service**.  
  
     La boîte de dialogue **Ajouter une référence de service** s'affiche.  
  
2.  Cliquez sur **Découvrir**.  
  
     Tous les services \(à la fois les services [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] et les services WCF\) dans la solution actuelle sont ajoutés à la liste des **Services**.  
  
3.  Dans la liste **Services**, développez le nœud du service que vous souhaitez utiliser et sélectionnez un jeu d'entités.  
  
4.  Dans la zone **Espace de noms**, entrez l'espace de noms que vous souhaitez utiliser pour la référence.  
  
5.  Cliquez sur **OK** pour ajouter la référence au projet.  
  
     Un client de service \(proxy\) est généré et les métadonnées qui décrivent le service sont ajoutées au fichier app.config.  
  
## Mise à jour d'une référence de service  
 Le modèle EDM \(Entity Data Model\) d'un service [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] change parfois.  Lorsque cela se produit, la référence de service doit être mise à jour.  
  
#### Pour mettre à jour une référence de service  
  
-   Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur la référence de service, puis cliquez sur **Mettre à jour la référence de service**.  
  
     Une boîte de dialogue de progression s'affiche pendant la mise à jour de la référence à partir de son emplacement d'origine et le client de service est régénéré pour répercuter toutes les modifications dans les métadonnées.  
  
## Suppression d'une référence de service  
 Si une référence de service n'est plus utilisée, vous pouvez la supprimer de votre solution.  
  
#### Pour supprimer une référence de service  
  
-   Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur la référence de service, puis cliquez sur **Supprimer**.  
  
     Le client de service est supprimé de la solution et les métadonnées qui décrivent le service sont supprimés du fichier app.config.  
  
    > [!NOTE]
    >  Tout code qui référence la référence de service doit être supprimé manuellement.  
  
## Voir aussi  
 [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)