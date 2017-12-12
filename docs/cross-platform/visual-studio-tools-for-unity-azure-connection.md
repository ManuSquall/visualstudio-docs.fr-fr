---
title: "Procédure pas à pas de connexion Visual Studio Tools pour Unity Azure| Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 516A8FB2-8DFF-4BAB-8116-FDCD1C228DB3
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: f21e320fe9e27f6873b9caed3048a93bfa94a9c4
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="test-the-client-connection"></a>Tester la connexion du client

Maintenant que le singleton AzureMobileServiceClient est créé, il est temps de tester la connexion du client.

## <a name="create-the-testclientconnection-script"></a>Créer le script TestClientConnection

1. Dans le dossier **Scripts** dans Unity, créez un script C# appelé **TestClientConnection**.

2. Ouvrez le script dans Visual Studio, supprimez tout code de modèle, puis ajoutez le code suivant :

  ```csharp
  using System.Collections.Generic;
  using UnityEngine;
  using System.Threading.Tasks;
  using System;
  using System.Linq;
  using Microsoft.WindowsAzure.MobileServices;

  public class TestClientConnection : MonoBehaviour
  {
      void Start()
      {
          Task.Run(TestTableConnection);
      }

      private async Task TestTableConnection()
      {
          var table = AzureMobileServiceClient.Client.GetTable<CrashInfo>();

          Debug.Log("Testing ToListAsync...");
          await TestToListAsync(table);

          Debug.Log("Testing InsertAsync...");
          await TestInsertAsync(table);

          Debug.Log("Testing DeleteAsync...");
          await TestDeleteAsync(table);

          Debug.Log("All testing complete.");
      }

      private async Task TestInsertAsync(IMobileServiceTable<CrashInfo> table)
      {
          try
          {
              var allEntries = await TestToListAsync(table);
              var initialCount = allEntries.Count();

              await table.InsertAsync(new CrashInfo { X = 1, Y = 2, Z = 3 });

              allEntries = await TestToListAsync(table);
              var newCount = allEntries.Count();

              Debug.Assert(newCount == initialCount + 1, "InsertAsync failed!");
          }
          catch (Exception)
          {
              throw;
          }
      }

      private async Task<List<CrashInfo>> TestToListAsync(IMobileServiceTable<CrashInfo> table)
      {
          try
          {
              var allEntries = await table.ToListAsync();
              Debug.Assert(allEntries != null, "ToListAsync failed!");
              return allEntries;
          }
          catch (Exception)
          {

              throw;
          }
      }

      private async Task TestDeleteAsync(IMobileServiceTable<CrashInfo> table)
      {
          var allEntries = await TestToListAsync(table);

          foreach (var item in allEntries)
          {
              try
              {
                  await table.DeleteAsync(item);
              }
              catch (Exception)
              {
                  throw;
              }
          }

          allEntries = await TestToListAsync(table);

          Debug.Assert(allEntries.Count() == 0, "DeleteAsync failed!");
      }
  }
  ```

3. Dans le menu **GameObject** d’Unity, sélectionnez **GameObject > Créer vide** pour créer un GameObject vide dans la scène Unity. Renommez-le **TestClientConnection**.

4. **Faites glisser** le script TestClientConnection à partir de la fenêtre **Projet** d’Unity vers le GameObject TestClientConnection dans la fenêtre **Hierarchy** (Hiérarchie).

5. Dans le menu Unity, sélectionnez **Fichier > Save Scene as...** (Enregistrer la scène sous). Nommez la scène **Test de la connexion du client** et cliquez sur **Enregistrer**.

5. Cliquez sur le bouton **Lire** dans Unity et examinez la fenêtre de console. Vérifiez qu’aucune des assertions n’a échoué.

6. Ouvrez la table facile CrashInfo dans le portail Azure. Elle doit maintenant afficher une entrée avec les coordonnées **X,Y,Z** définies sur les valeurs **(1, 2, 3)** et la valeur **true** dans la colonne **Deleted** (Supprimé). Chaque fois que vous exécutez le test, une nouvelle entrée avec les mêmes valeurs, mais un ID unique, doit être ajoutée à la table.

  ![Entrée de table facile](media/vstu_azure-test-client-connection-image1.png)

## <a name="next-step"></a>Étape suivante
* [Importer les ressources de l’exemple de jeu](visual-studio-tools-for-unity-azure-game-assets.md).
