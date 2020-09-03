---
title: 'Comment : se connecter à des données dans un service'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data [Visual Studio], connecting to web services
- data sources, creating from web services
- data [Visual Studio], reading from web services
- reading data, from web services
- web services, reading data
- web services, as data sources
- web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 0b49840a2190abfd223edf5643b8d70da1a59d6b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282226"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Guide pratique pour se connecter à des données dans un service

Pour connecter votre application aux données retournées par un service, exécutez l' [Assistant Configuration de source de données](../data-tools/media/data-source-configuration-wizard.png) et sélectionnez **service** dans la page **choisir un type de source de données** .

Une fois l’Assistant terminé, une référence de service est ajoutée à votre projet et est immédiatement disponible dans la [fenêtre sources de données](add-new-data-sources.md#data-sources-window).

> [!NOTE]
> Les éléments qui s’affichent dans la fenêtre **Sources de données** dépendent des informations retournées par le service. Certains services peuvent ne pas fournir suffisamment d’informations pour que l’**Assistant Configuration de source de données** puisse créer des objets pouvant être liés. Par exemple, si le service retourne un DataSet non typé, aucun élément ne s’affiche dans la fenêtre **sources de données** lors de la fin de l’Assistant. En effet, comme les datasets non typés ne fournissent pas de schéma, l’Assistant ne dispose pas de suffisamment d’informations pour créer la source de données.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>Pour connecter votre application à un service

1. Dans le menu **Données** , cliquez sur **Ajouter une nouvelle source de données**.

2. Sélectionnez **service** dans la page **choisir un type de source de données** , puis cliquez sur **suivant**.

3. Entrez l’adresse du service que vous souhaitez utiliser ou cliquez sur **découvrir** pour rechercher des services dans la solution actuelle, puis cliquez sur **OK**.

4. Si vous le souhaitez, vous pouvez taper un nouvel **espace de noms** à la place de la valeur par défaut.

    > [!NOTE]
    > Cliquez sur **avancé** pour ouvrir la boîte de [dialogue Configurer la référence de service](../data-tools/configure-service-reference-dialog-box.md).

5. Cliquez sur **OK** pour ajouter une référence de service à votre projet.

6. Cliquez sur **Terminer**.

     La source de données est ajoutée à la fenêtre **Sources de données**.

## <a name="next-steps"></a>Étapes suivantes

Pour ajouter des fonctionnalités à votre application, sélectionnez un élément dans la fenêtre **sources de données** et faites-le glisser sur un formulaire pour créer des contrôles liés. Pour plus d’informations, consultez [lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles WPF à un service de données WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Services de Windows Communication Foundation et services de données WCF dans Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
