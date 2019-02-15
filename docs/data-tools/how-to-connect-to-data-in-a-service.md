---
title: 'Comment : se connecter à des données dans un service'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], connecting to web services
- data sources, creating from web services
- data [Visual Studio], reading from web services
- reading data, from web services
- web services, reading data
- web services, as data sources
- web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f3fd643ca29c5f5e4df20f244bc06b6bca04b9bd
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55930738"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Guide pratique pour se connecter à des données dans un service

Vous connectez votre application aux données retournées à partir d’un service en exécutant la [Assistant de Configuration de Source de données](../data-tools/media/data-source-configuration-wizard.png) et en sélectionnant **Service** sur la **choisir un Type de Source de données**page.

À l’achèvement de l’Assistant, une référence de service est ajoutée à votre projet et est immédiatement disponible dans le [fenêtre Sources de données](add-new-data-sources.md#data-sources-window).

> [!NOTE]
> Les éléments qui s’affichent dans la fenêtre **Sources de données** dépendent des informations retournées par le service. Certains services peuvent ne pas fournir suffisamment d’informations pour que l’**Assistant Configuration de source de données** puisse créer des objets pouvant être liés. Par exemple, si le service retourne un dataset non typé, aucun élément ne s’affichent dans le **des Sources de données** fenêtre à la fin de l’Assistant. Il s’agit, car les datasets non typés ne fournissent pas de schéma, afin de l’Assistant n’a pas suffisamment d’informations pour créer la source de données.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>Pour connecter votre application à un service

1.  Dans le menu **Données** , cliquez sur **Ajouter une nouvelle source de données**.

2.  Sélectionnez **Service** sur le **choisir un Type de Source de données** page, puis cliquez sur **suivant**.

3.  Entrez l’adresse du service que vous souhaitez utiliser, ou cliquez sur **Discover** à localiser les services dans la solution actuelle, puis cliquez sur **accédez**.

4.  Si vous le souhaitez, vous pouvez taper un nouveau **Namespace** à la place de la valeur par défaut.

    > [!NOTE]
    > Cliquez sur **avancé** pour ouvrir le [boîte de dialogue Configurer la référence de Service](../data-tools/configure-service-reference-dialog-box.md).

5.  Cliquez sur **OK** pour ajouter une référence de service à votre projet.

6.  Cliquez sur **Terminer**.

     La source de données est ajoutée à la fenêtre **Sources de données**.

## <a name="next-steps"></a>Étapes suivantes

Pour ajouter des fonctionnalités à votre application, sélectionnez un élément dans le **des Sources de données** fenêtre et faites-le glisser sur un formulaire pour créer des contrôles liés. Pour plus d’informations, consultez [lier des contrôles aux données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles WPF à un service de données WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Services Windows Communication Foundation et services de données WCF dans Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)