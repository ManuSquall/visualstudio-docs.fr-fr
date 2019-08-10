---
title: 'Procédure : ajouter, mettre à jour ou supprimer une référence de service de données WCF'
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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: da8555d4246d2177b3d97eeef8d24c7b4a22b31d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925637"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Procédure : ajouter, mettre à jour ou supprimer une référence de service de données WCF
Une *référence de service* permet à un projet d’accéder à [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]un ou plusieurs. Utilisez la boîte de dialogue **Ajouter une référence de service** pour rechercher [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] dans la solution actuelle, localement, sur un réseau local ou sur Internet.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-a-service-reference"></a>Ajouter une référence de service

### <a name="to-add-a-reference-to-an-external-service"></a>Pour ajouter une référence à un service externe

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nom du projet auquel vous souhaitez ajouter le service, puis cliquez sur **Ajouter une référence de service**.

     La boîte de dialogue **Ajouter une référence de service** s’affiche.

2. Dans la zone **adresse** , entrez l’URL du service, puis cliquez sur **atteindre** pour rechercher le service. Si le service implémente la sécurité du nom d’utilisateur et du mot de passe, vous pouvez être invité à entrer un nom d’utilisateur et un mot de passe.

    > [!NOTE]
    > Vous devez référencer des services uniquement à partir d’une source approuvée. L’ajout de références à partir d’une source non fiable peut compromettre la sécurité.

     Vous pouvez également sélectionner l’URL dans la liste d' **adresses** , qui stocke les 15 URL précédentes auxquelles des métadonnées de service valides ont été trouvées.

     Une barre de progression s’affiche lorsque la recherche est en cours d’exécution. Vous pouvez arrêter la recherche à tout moment en cliquant sur **arrêter**.

3. Dans la liste des **services** , développez le nœud du service que vous souhaitez utiliser, puis sélectionnez un jeu d’entités.

4. Dans la zone **espace de noms** , entrez l’espace de noms que vous souhaitez utiliser pour la référence.

5. Cliquez sur **OK** pour ajouter la référence au projet.

     Un client de service (proxy) est généré, et les métadonnées qui décrivent le service sont ajoutées au fichier *app. config* .

### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Pour ajouter une référence à un service dans la solution actuelle

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nom du projet auquel vous souhaitez ajouter le service, puis cliquez sur **Ajouter une référence de service**.

    La boîte de dialogue **Ajouter une référence de service** s’affiche.

2. Cliquez sur **découvrir**.

    Tous les services ( [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] et les services WCF) de la solution actuelle sont ajoutés à la liste des **services** .

3. Dans la liste des **services** , développez le nœud du service que vous souhaitez utiliser, puis sélectionnez un jeu d’entités.

4. Dans la zone **espace de noms** , entrez l’espace de noms que vous souhaitez utiliser pour la référence.

5. Cliquez sur **OK** pour ajouter la référence au projet.

    Un client de service (proxy) génère, et les métadonnées qui décrivent le service sont ajoutées au fichier *app. config* .

## <a name="update-a-service-reference"></a>Mettre à jour une référence de service
La Entity Data Model pour une [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] modification parfois. Dans ce cas, vous devez mettre à jour la référence de service.

### <a name="to-update-a-service-reference"></a>Pour mettre à jour une référence de service

- Dans **Explorateur de solutions**, cliquez avec le bouton droit sur la référence de service, puis cliquez sur **mettre à jour la référence de service**.

     Une boîte de dialogue de progression s’affiche lorsque la référence est mise à jour à partir de son emplacement d’origine, et le client de service est régénéré pour refléter les modifications apportées aux métadonnées.

## <a name="remove-a-service-reference"></a>Supprimer une référence de service
Si une référence de service n’est plus utilisée, vous pouvez la supprimer de votre solution.

### <a name="to-remove-a-service-reference"></a>Pour supprimer une référence de service

- Dans **Explorateur de solutions**, cliquez avec le bouton droit sur la référence de service, puis cliquez sur **supprimer**.

     Le client de service sera supprimé de la solution, et les métadonnées qui décrivent le service seront supprimées du fichier *app. config* .

    > [!NOTE]
    > Tout code qui fait référence à la référence de service doit être supprimé manuellement.

## <a name="see-also"></a>Voir aussi

- [Services Windows Communication Foundation et services de données WCF dans Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)