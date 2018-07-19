---
title: 'Comment : ajouter, mettre à jour ou supprimer une référence de service de données WCF'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b6726b2c859143f5dbc9b264e67bb9bb91757de5
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089310"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Comment : ajouter, mettre à jour ou supprimer une référence de service de données WCF
Un *référence de service* permet à un projet à l’accès à un ou plusieurs [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]. Utilisez le **ajouter une référence de Service** boîte de dialogue pour rechercher des [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] dans la solution actuelle, localement, sur un réseau local ou sur Internet.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-a-service-reference"></a>Ajouter une référence de service

### <a name="to-add-a-reference-to-an-external-service"></a>Pour ajouter une référence à un service externe

1.  Dans **l’Explorateur de solutions**, cliquez sur le nom du projet auquel vous souhaitez ajouter le service, puis cliquez sur **ajouter une référence de Service**.

     Le **ajouter une référence de Service** boîte de dialogue s’affiche.

2.  Dans le **adresse** zone, entrez l’URL du service, puis cliquez sur **accédez** pour rechercher le service. Si le service implémente la sécurité de nom et mot de passe utilisateur, vous devrez peut-être utiliser un nom d’utilisateur et mot de passe.

    > [!NOTE]
    >  Vous devez référencer des services uniquement à partir d’une source approuvée. L’ajout de références à partir d’une source non fiable peut compromettre la sécurité.

     Vous pouvez également sélectionner l’URL à partir de la **adresse** liste, qui stocke les 15 URL précédentes à partir duquel les métadonnées de service valide a été trouvée.

     Une barre de progression affiche lors de la recherche est en cours d’exécution. Vous pouvez arrêter la recherche à tout moment en cliquant sur **arrêter**.

3.  Dans le **Services** liste, développez le nœud pour le service que vous souhaitez utiliser, puis sélectionnez un jeu d’entités.

4.  Dans le **Namespace** , entrez l’espace de noms que vous souhaitez utiliser pour la référence.

5.  Cliquez sur **OK** pour ajouter la référence au projet.

     Un client de service (proxy) est généré et les métadonnées qui décrivent le service sont ajoutée à la *app.config* fichier.

### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Pour ajouter une référence à un service dans la solution actuelle

1.  Dans **l’Explorateur de solutions**, cliquez sur le nom du projet auquel vous souhaitez ajouter le service, puis cliquez sur **ajouter une référence de Service**.

     Le **ajouter une référence de Service** boîte de dialogue s’affiche.

2.  Cliquez sur **découvrir**.

     Tous les services (les deux [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] et les services WCF) dans la solution actuelle sont ajoutés à la **Services** liste.

3.  Dans le **Services** liste, développez le nœud pour le service que vous souhaitez utiliser, puis sélectionnez un jeu d’entités.

4.  Dans le **Namespace** , entrez l’espace de noms que vous souhaitez utiliser pour la référence.

5.  Cliquez sur **OK** pour ajouter la référence au projet.

     Génère un client de service (proxy), et les métadonnées qui décrivent le service sont ajoutée à la *app.config* fichier.

## <a name="update-a-service-reference"></a>Mise à jour une référence de service
 L’Entity Data Model pour un [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] parfois change. Dans ce cas, vous devez mettre à jour la référence de service.

### <a name="to-update-a-service-reference"></a>Pour mettre à jour une référence de service

-   Dans **l’Explorateur de solutions**, avec le bouton droit de la référence de service, puis cliquez sur **référence de Service de mise à jour**.

     Une boîte de dialogue de progression affiche alors que la référence est mis à jour à partir de son emplacement d’origine et le client du service est régénéré pour refléter ces modifications dans les métadonnées.

## <a name="remove-a-service-reference"></a>Supprimer une référence de service
 Si une référence de service est n’est plus utilisée, vous pouvez le supprimer à partir de votre solution.

### <a name="to-remove-a-service-reference"></a>Pour supprimer une référence de service

-   Dans **l’Explorateur de solutions**, avec le bouton droit de la référence de service, puis cliquez sur **supprimer**.

     Le client du service sera retiré de la solution et les métadonnées qui décrivent le service seront retirée le *app.config* fichier.

    > [!NOTE]
    >  Tout code qui fait référence à la référence de service doit être supprimé manuellement.

## <a name="see-also"></a>Voir aussi

- [Services de données de Services Windows Communication Foundation et WCF dans Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)