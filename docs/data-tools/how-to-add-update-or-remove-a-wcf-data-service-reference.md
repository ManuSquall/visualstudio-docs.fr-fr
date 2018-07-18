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
ms.openlocfilehash: 9e39b28a3de5aa97ac7c0673cd16b71508ae4276
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31925974"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Comment : ajouter, mettre à jour ou supprimer une référence de service de données WCF
A *référence de service* permet à un projet pour accéder à un ou plusieurs [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]. Utilisez le **ajouter une référence de Service** boîte de dialogue pour rechercher des [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] dans la solution actuelle, localement, sur un réseau local ou sur Internet.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="adding-a-service-reference"></a>Ajout d’une référence de Service

#### <a name="to-add-a-reference-to-an-external-service"></a>Pour ajouter une référence à un service externe

1.  Dans **l’Explorateur de solutions**, cliquez sur le nom du projet que vous souhaitez ajouter le service, puis cliquez sur **ajouter une référence de Service**.

     Le **ajouter une référence de Service** boîte de dialogue s’affiche.

2.  Dans le **adresse** zone, entrez l’URL du service, puis cliquez sur **accédez** pour rechercher le service. Si le service implémente la sécurité de nom et mot de passe utilisateur, vous pouvez être invité pour un nom d’utilisateur et un mot de passe.

    > [!NOTE]
    >  Vous devez référencer des services uniquement à partir d’une source approuvée. L’ajout de références à partir d’une source non fiable peut compromettre la sécurité.

     Vous pouvez également sélectionner l’URL à partir de la **adresse** liste, qui stocke les 15 URL précédentes, à laquelle les métadonnées de service valide a été trouvée.

     Une barre de progression s’affiche lors de la recherche est effectuée. Vous pouvez arrêter la recherche à tout moment en cliquant sur **arrêter**.

3.  Dans le **Services** liste, développez le nœud pour le service que vous souhaitez utiliser, puis sélectionnez un jeu d’entités.

4.  Dans le **Namespace** , entrez l’espace de noms que vous souhaitez utiliser pour la référence.

5.  Cliquez sur **OK** pour ajouter la référence au projet.

     Un client de service (proxy) est généré et les métadonnées qui décrivent le service sont ajoutées au fichier app.config.

#### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Pour ajouter une référence à un service dans la solution actuelle

1.  Dans **l’Explorateur de solutions**, cliquez sur le nom du projet que vous souhaitez ajouter le service, puis cliquez sur **ajouter une référence de Service**.

     Le **ajouter une référence de Service** boîte de dialogue s’affiche.

2.  Cliquez sur **découvrir**.

     Tous les services (à la fois [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] et les services WCF) dans la solution actuelle sont ajoutés à la **Services** liste.

3.  Dans le **Services** liste, développez le nœud pour le service que vous souhaitez utiliser, puis sélectionnez un jeu d’entités.

4.  Dans le **Namespace** , entrez l’espace de noms que vous souhaitez utiliser pour la référence.

5.  Cliquez sur **OK** pour ajouter la référence au projet.

     Un client de service (proxy) est généré et les métadonnées qui décrivent le service sont ajoutées au fichier app.config.

## <a name="updating-a-service-reference"></a>Mise à jour d’une référence de Service
 L’Entity Data Model pour un [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] change parfois. Dans ce cas, la référence de service doit être mis à jour.

#### <a name="to-update-a-service-reference"></a>Pour mettre à jour une référence de service

-   Dans **l’Explorateur de solutions**, avec le bouton droit de la référence de service, puis sur **référence de Service de mise à jour**.

     Une boîte de dialogue de progression s’affiche pendant que la référence est mise à jour à partir de son emplacement d’origine et le client du service est régénéré pour refléter les modifications dans les métadonnées.

## <a name="removing-a-service-reference"></a>Suppression d’une référence de Service
 Si une référence de service est n’est plus utilisée, vous pouvez le supprimer de votre solution.

#### <a name="to-remove-a-service-reference"></a>Pour supprimer une référence de service

-   Dans **l’Explorateur de solutions**, avec le bouton droit de la référence de service, puis sur **supprimer**.

     Le client du service sera retiré de la solution et les métadonnées qui décrivent le service seront retirée le fichier app.config.

    > [!NOTE]
    >  Tout code qui fait référence à la référence de service aura doit être supprimé manuellement.

## <a name="see-also"></a>Voir aussi

- [Services Windows Communication Foundation et services de données WCF dans Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)