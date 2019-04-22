---
title: 'Procédure : Se connecter aux données dans un Service | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a13d0c8ff1383e27f9401f6549c422a8fef96e99
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59650042"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Procédure : se connecter à des données dans un service
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous connectez votre application aux données retournées à partir d’un service en exécutant la [Assistant de Configuration de Source de données](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) et en sélectionnant **Service** sur la **choisir un Type de Source de données**page.  
  
 À l’achèvement de l’Assistant, une référence de service est ajoutée à votre projet et est immédiatement disponible dans le [fenêtre Sources de données](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
> [!NOTE]
>  Les éléments qui s’affichent dans la fenêtre **Sources de données** dépendent des informations retournées par le service. Certains services peuvent ne pas fournir suffisamment d’informations pour que l’**Assistant Configuration de source de données** puisse créer des objets pouvant être liés. Par exemple, si le service retourne un dataset non typé, puis aucun élément n’apparaître dans le **fenêtre Sources de données** à la fin de l’Assistant. Il s’agit, car les datasets non typés ne fournissent pas de schéma, afin de l’Assistant n’a pas suffisamment d’informations pour créer la source de données.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-connect-your-application-to-a-service"></a>Pour connecter votre application à un service  
  
1.  Dans le menu **Données** , cliquez sur **Ajouter une nouvelle source de données**.  
  
2.  Sélectionnez **Service** sur le **choisir un Type de Source de données** page, puis cliquez sur **suivant**.  
  
3.  Entrez l’adresse du service que vous souhaitez utiliser, ou cliquez sur **Discover** à localiser les services dans la solution actuelle, puis cliquez sur **accédez**.  
  
4.  Si vous le souhaitez, une nouvelle **Namespace** peuvent être tapés à la place de la valeur par défaut.  
  
    > [!NOTE]
    >  Cliquez sur **avancé** pour ouvrir le [configurer une référence de Service, boîte de dialogue](../data-tools/configure-service-reference-dialog-box.md).  
  
5.  Cliquez sur **OK** pour ajouter une référence de service à votre projet.  
  
6.  Cliquez sur **Terminer**.  
  
     La source de données est ajoutée à la fenêtre **Sources de données**.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
#### <a name="to-add-functionality-to-your-application"></a>Pour ajouter une fonctionnalité à votre application  
  
-   Sélectionnez un élément dans le **des Sources de données** fenêtre et faites-le glisser sur un formulaire pour créer des contrôles liés. Pour plus d’informations, consultez [lier des contrôles aux données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Lier des contrôles WPF à un service de données WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Services Windows Communication Foundation et services de données WCF dans Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
