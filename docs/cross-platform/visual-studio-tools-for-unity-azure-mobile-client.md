---
title: "Procédure pas à pas de MobileServiceClient Visual Studio Tools pour Unity Azure| Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5A8762A1-D843-4FD8-A89B-E5E489ECA03D
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 294942641aa0739d105a888f4fbfe6ba9cf05a16
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="implement-the-azure-mobileserviceclient"></a>Implémenter Azure MobileServiceClient

Au centre du kit SDK Azure Mobile Client figure <a href="https://msdn.microsoft.com/en-us/library/azure/microsoft.windowsazure.mobileservices.mobileserviceclient(v=azure.10).aspx">MobileServiceClient</a>, qui permet d’accéder à votre back-end Mobile App.

## <a name="locate-the-url-of-the-mobile-app-backend"></a>Rechercher l’URL du back-end Mobile App

Comme le constructeur `MobileServiceClient` accepte l’URL de l’application mobile en tant que paramètre, recherchez-la avant de poursuivre.

1. Dans le portail Azure, cliquez sur le bouton **App Services**.

    ![Cliquer sur App Services](media/vstu_azure-implement-azure-mobileserviceclient-image1.png)

2. Cliquez sur l’entrée pour votre application mobile.

    ![Cliquer sur l’application mobile](media/vstu_azure-implement-azure-mobileserviceclient-image2.png)

3. Copiez l’URL de votre back-end Mobile App.

    ![Copier l’URL](media/vstu_azure-implement-azure-mobileserviceclient-image3.png)

## <a name="create-the-mobileserviceclient-singleton"></a>Créer le singleton MobileServiceClient

Comme il ne doit exister qu’une seule instance de `MobileServiceClient`, la procédure pas à pas utilise une variante du modèle de singleton.

1. Dans le répertoire **Assets/Scripts** (Ressources/Scripts) de votre projet Unity, créez un script C# nommé **AzureMobileServiceClient**.

2. Ouvrez le script `AzureMobileServiceClient` et supprimez tout code de modèle, dont la déclaration de classe et les instructions using.

3. Ajoutez le code suivant :

  ```csharp
  using Microsoft.WindowsAzure.MobileServices;

  public static class AzureMobileServiceClient
  {
      private const bool ignoreTls = true;
      private const string backendUrl = "MOBILE_APP_URL";
      private static MobileServiceClient client;

      public static MobileServiceClient Client
      {
          get
          {
              if (client == null)
              {
                  client = new MobileServiceClient(backendUrl);
              }

              return client;
          }
      }
  }
  ```

  > [!NOTE]
  > Si IntelliSense ne reconnaît pas l’espace de noms Microsoft.WindowsAzure, vérifiez que vous avez effectué toutes les étapes de la section [Préparer l’environnement de développement]().

4. Dans le code précédent, remplacez `MOBILE_APP_URL` par l’URL de votre back-end Mobile App.

## <a name="next-step"></a>Étape suivante

* [Mettre à jour le magasin de certificats de sécurité Mono d’Unity](visual-studio-tools-for-unity-azure-security.md)
