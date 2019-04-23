---
title: 'Procédure : Ajouter, mettre à jour ou supprimer une référence de Service de données WCF | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 33c0f0235e2f4fe2fb633a94a024563b4fb9b276
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59664923"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Procédure : ajouter, mettre à jour ou supprimer une référence de service de données WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un *référence de service* permet à un projet à l’accès à un ou plusieurs [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)]. Utilisez le **ajouter une référence de Service** boîte de dialogue pour rechercher des [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] dans la solution actuelle, localement, sur un réseau local ou sur Internet.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="adding-a-service-reference"></a>Ajout d’une référence de Service  
  
#### <a name="to-add-a-reference-to-an-external-service"></a>Pour ajouter une référence à un service externe  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur le nom du projet que vous souhaitez ajouter le service, puis cliquez sur **ajouter une référence de Service**.  
  
     Le **ajouter une référence de Service** boîte de dialogue s’affiche.  
  
2.  Dans le **adresse** zone, entrez l’URL du service, puis cliquez sur **accédez** pour rechercher le service. Si le service implémente la sécurité de nom et mot de passe utilisateur, vous devrez peut-être utiliser un nom d’utilisateur et mot de passe.  
  
    > [!NOTE]
    >  Vous devez référencer des services uniquement à partir d’une source approuvée. L’ajout de références à partir d’une source non fiable peut compromettre la sécurité.  
  
     Vous pouvez également sélectionner l’URL à partir de la **adresse** liste, qui stocke les 15 URL précédentes à partir duquel les métadonnées de service valide a été trouvée.  
  
     Une barre de progression s’affiche lors de la recherche est en cours d’exécution. Vous pouvez arrêter la recherche à tout moment en cliquant sur **arrêter**.  
  
3.  Dans le **Services** liste, développez le nœud pour le service que vous souhaitez utiliser, puis sélectionnez un jeu d’entités.  
  
4.  Dans le **Namespace** , entrez l’espace de noms que vous souhaitez utiliser pour la référence.  
  
5.  Cliquez sur **OK** pour ajouter la référence au projet.  
  
     Un client de service (proxy) est généré et les métadonnées qui décrivent le service sont ajoutée au fichier app.config.  
  
#### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Pour ajouter une référence à un service dans la solution actuelle  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur le nom du projet que vous souhaitez ajouter le service, puis cliquez sur **ajouter une référence de Service**.  
  
     Le **ajouter une référence de Service** boîte de dialogue s’affiche.  
  
2.  Cliquez sur **découvrir**.  
  
     Tous les services (les deux [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] et les services WCF) dans la solution actuelle sont ajoutés à la **Services** liste.  
  
3.  Dans le **Services** liste, développez le nœud pour le service que vous souhaitez utiliser, puis sélectionnez un jeu d’entités.  
  
4.  Dans le **Namespace** , entrez l’espace de noms que vous souhaitez utiliser pour la référence.  
  
5.  Cliquez sur **OK** pour ajouter la référence au projet.  
  
     Un client de service (proxy) est généré et les métadonnées qui décrivent le service sont ajoutée au fichier app.config.  
  
## <a name="updating-a-service-reference"></a>La mise à jour une référence de Service  
 L’Entity Data Model pour un [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] change parfois. Dans ce cas, la référence de service doit être mis à jour.  
  
#### <a name="to-update-a-service-reference"></a>Pour mettre à jour une référence de service  
  
-   Dans **l’Explorateur de solutions**, avec le bouton droit de la référence de service, puis cliquez sur **référence de Service de mise à jour**.  
  
     Une boîte de dialogue de progression s’affiche pendant la référence est mis à jour à partir de son emplacement d’origine et le client du service est régénéré pour refléter ces modifications dans les métadonnées.  
  
## <a name="removing-a-service-reference"></a>Suppression d’une référence de Service  
 Si une référence de service est n’est plus utilisée, vous pouvez le supprimer à partir de votre solution.  
  
#### <a name="to-remove-a-service-reference"></a>Pour supprimer une référence de service  
  
-   Dans **l’Explorateur de solutions**, avec le bouton droit de la référence de service, puis cliquez sur **supprimer**.  
  
     Le client du service sera retiré de la solution et les métadonnées qui décrivent le service seront retirée le fichier app.config.  
  
    > [!NOTE]
    >  Tout code qui fait référence à la référence de service doivent être supprimés manuellement.  
  
## <a name="see-also"></a>Voir aussi  
 [Services Windows Communication Foundation et services de données WCF dans Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
