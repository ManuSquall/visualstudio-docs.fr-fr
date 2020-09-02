---
title: 'Comment : ajouter, mettre à jour ou supprimer une référence de service de données WCF'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f5f5a1e14a6eab7537c8ce64636f0f34378ad7f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282369"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Guide pratique pour ajouter, mettre à jour ou supprimer une référence de service de données WCF

::: moniker range="vs-2017"
Une *référence de service* permet à un projet d’accéder à un ou plusieurs [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] . Utilisez la boîte de dialogue **Ajouter une référence de service** pour rechercher [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] dans la solution actuelle, localement, sur un réseau local ou sur Internet.
::: moniker-end
::: moniker range=">=vs-2019"
Vous pouvez utiliser le nœud **services connectés** dans **Explorateur de solutions** pour accéder au **Microsoft WCF Web Service Reference Provider**, qui vous permet de gérer les références de service de données Windows Communication Foundation (WCF).
::: moniker-end

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-a-wcf-service-reference"></a>Ajouter une référence de service WCF

### <a name="to-add-a-reference-to-an-external-service"></a>Pour ajouter une référence à un service externe

::: moniker range="vs-2017"

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nom du projet auquel vous souhaitez ajouter le service, puis cliquez sur **Ajouter une référence de service**.

   **La boîte de dialogue **Ajouter une référence de service s'affiche.

1. Dans la zone **adresse** , entrez l’URL du service, puis cliquez sur **atteindre** pour rechercher le service. Si le service implémente la sécurité du nom d’utilisateur et du mot de passe, vous pouvez être invité à entrer un nom d’utilisateur et un mot de passe.

    > [!NOTE]
    > Vous devez référencer des services uniquement à partir d’une source approuvée. L’ajout de références à partir d’une source non fiable peut compromettre la sécurité.

     Vous pouvez également sélectionner l’URL dans la liste d' **adresses** , qui stocke les 15 URL précédentes auxquelles des métadonnées de service valides ont été trouvées.

     Une barre de progression s’affiche lorsque la recherche est en cours d’exécution. Vous pouvez arrêter la recherche à tout moment en cliquant sur **arrêter**.

1. Dans la liste des **services** , développez le nœud du service que vous souhaitez utiliser, puis sélectionnez un jeu d’entités.

1. Dans la zone **Espace de noms**, entrez l'espace de noms que vous souhaitez utiliser pour la référence.

1. Cliquez sur **Ok** pour ajouter la référence au projet.

     Un client de service (proxy) est généré, et les métadonnées qui décrivent le service sont ajoutées au fichier *app.config* .
::: moniker-end
::: moniker range=">=vs-2019"
1. Dans **Explorateur de solutions**, double-cliquez ou appuyez sur le nœud **services connectés** .

   L’onglet **configurer les services** s’ouvre.

1. Choisissez **Microsoft WCF Web Service Reference Provider**.

   La boîte de dialogue **configurer la référence de service Web WCF** s’affiche.

   ![Capture d’écran de la boîte de dialogue fournisseur de services Web WCF](media/vs-2019/configure-wcf-web-service-reference-dialog.png)


1. Dans la zone **URI** , entrez l’URL du service, puis cliquez sur **atteindre** pour rechercher le service. Si le service implémente la sécurité du nom d’utilisateur et du mot de passe, vous pouvez être invité à entrer un nom d’utilisateur et un mot de passe.

    > [!NOTE]
    > Vous devez référencer des services uniquement à partir d’une source approuvée. L’ajout de références à partir d’une source non fiable peut compromettre la sécurité.

     Vous pouvez également sélectionner l’URL à partir de la liste **URI** , qui stocke les 15 URL précédentes auxquelles des métadonnées de service valides ont été trouvées.

     Une barre de progression s’affiche lorsque la recherche est en cours d’exécution. Vous pouvez arrêter la recherche à tout moment en cliquant sur **arrêter**.

1. Dans la liste des **services** , développez le nœud du service que vous souhaitez utiliser, puis sélectionnez un jeu d’entités.

1. Dans la zone **Espace de noms**, entrez l'espace de noms que vous souhaitez utiliser pour la référence.

1. Cliquez sur **Terminer** pour ajouter la référence au projet.

     Un client de service (proxy) est généré, et les métadonnées qui décrivent le service sont ajoutées au fichier *app.config* .

::: moniker-end

### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Pour ajouter une référence à un service dans la solution actuelle

::: moniker range="vs-2017"

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nom du projet auquel vous souhaitez ajouter le service, puis cliquez sur **Ajouter une référence de service**.

    **La boîte de dialogue **Ajouter une référence de service s'affiche.

1. Cliquez sur **découvrir**.

    Tous les services ( [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] et les services WCF) de la solution actuelle sont ajoutés à la liste des **services** .

1. Dans la liste des **services** , développez le nœud du service que vous souhaitez utiliser, puis sélectionnez un jeu d’entités.

1. Dans la zone **Espace de noms**, entrez l'espace de noms que vous souhaitez utiliser pour la référence.

1. Cliquez sur **Ok** pour ajouter la référence au projet.

    Un client de service (proxy) génère, et les métadonnées qui décrivent le service sont ajoutées au fichier *app.config* .
::: moniker-end
::: moniker range=">=vs-2019"
1. Dans **Explorateur de solutions**, double-cliquez ou appuyez sur le nœud **services connectés** . 

   L’onglet **configurer les services** s’ouvre.

1. Choisissez **Microsoft WCF Web Service Reference Provider**.

   La boîte de dialogue **configurer la référence de service Web WCF** s’affiche.

1. Cliquez sur **découvrir**.

    Tous les services ( [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] et les services WCF) de la solution actuelle sont ajoutés à la liste des **services** .

1. Dans la liste des **services** , développez le nœud du service que vous souhaitez utiliser, puis sélectionnez un jeu d’entités.

1. Dans la zone **Espace de noms**, entrez l'espace de noms que vous souhaitez utiliser pour la référence.

1. Cliquez sur **Terminer** pour ajouter la référence au projet.

    Un client de service (proxy) génère, et les métadonnées qui décrivent le service sont ajoutées au fichier *app.config* .

::: moniker-end

## <a name="update-a-service-reference"></a>Mettre à jour une référence de service

La Entity Data Model pour une [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] modification parfois. Dans ce cas, vous devez mettre à jour la référence de service.

### <a name="to-update-a-service-reference"></a>Pour mettre à jour une référence de service

- Dans **Explorateur de solutions**, cliquez avec le bouton droit sur la référence de service, puis cliquez sur **mettre à jour la référence de service**.

     Une boîte de dialogue de progression s’affiche lorsque la référence est mise à jour à partir de son emplacement d’origine, et le client de service est régénéré pour refléter les modifications apportées aux métadonnées.

## <a name="remove-a-service-reference"></a>Supprimer une référence de service

Si une référence de service n’est plus utilisée, vous pouvez la supprimer de votre solution.

### <a name="to-remove-a-service-reference"></a>Pour supprimer une référence de service

- Dans **Explorateur de solutions**, cliquez avec le bouton droit sur la référence de service, puis cliquez sur **supprimer**.

     Le client de service sera supprimé de la solution, et les métadonnées qui décrivent le service seront supprimées du fichier *app.config* .

    > [!NOTE]
    > Tout code qui fait référence à la référence de service doit être supprimé manuellement.

## <a name="see-also"></a>Voir aussi

- [Services de Windows Communication Foundation et services de données WCF dans Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
