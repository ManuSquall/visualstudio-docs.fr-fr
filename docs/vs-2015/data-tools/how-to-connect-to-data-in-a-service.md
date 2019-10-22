---
title: 'Comment : se connecter à des données dans un service | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], connecting to Web services
- data sources, creating from Web services
- data [Visual Studio], reading from Web services
- reading data, from Web services
- Web services, reading data
- Web services, as data sources
- Web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9bfa6c776e3a2137f751d4253feb0239811d95a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654687"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Comment : se connecter à des données dans un service
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour connecter votre application aux données retournées par un service, exécutez l' [Assistant Configuration de source de données](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) et sélectionnez **service** dans la page **choisir un type de source de données** .

 Une fois l’Assistant terminé, une référence de service est ajoutée à votre projet et est immédiatement disponible dans la [fenêtre sources de données](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

> [!NOTE]
> Les éléments qui s’affichent dans la fenêtre **Sources de données** dépendent des informations retournées par le service. Certains services peuvent ne pas fournir suffisamment d’informations pour que l’**Assistant Configuration de source de données** puisse créer des objets pouvant être liés. Par exemple, si le service retourne un DataSet non typé, aucun élément ne s’affiche dans la **fenêtre sources de données** lors de la fin de l’Assistant. En effet, comme les datasets non typés ne fournissent pas de schéma, l’Assistant ne dispose pas de suffisamment d’informations pour créer la source de données.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-connect-your-application-to-a-service"></a>Pour connecter votre application à un service

1. Dans le menu **Données** , cliquez sur **Ajouter une nouvelle source de données**.

2. Sélectionnez **service** dans la page **choisir un type de source de données** , puis cliquez sur **suivant**.

3. Entrez l’adresse du service que vous souhaitez utiliser ou cliquez sur **découvrir** pour rechercher des services dans la solution actuelle, puis cliquez sur **OK**.

4. Un nouvel **espace de noms** peut éventuellement être entré à la place de la valeur par défaut.

    > [!NOTE]
    > Cliquez sur **avancé** pour ouvrir la boîte de [dialogue Configurer la référence de service](../data-tools/configure-service-reference-dialog-box.md).

5. Cliquez sur **OK** pour ajouter une référence de service à votre projet.

6. Cliquez sur **Finish**.

     La source de données est ajoutée à la fenêtre **Sources de données**.

## <a name="next-steps"></a>Étapes suivantes

#### <a name="to-add-functionality-to-your-application"></a>Pour ajouter une fonctionnalité à votre application

- Sélectionnez un élément dans la fenêtre **sources de données** et faites-le glisser sur un formulaire pour créer des contrôles liés. Pour plus d’informations, consultez [lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
 [Lier des contrôles WPF à un service de données WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) [Windows Communication Foundation services et WCF Data Services dans Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
