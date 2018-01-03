---
title: "Procédure pas à pas de HeatmapScene Visual Studio Tools pour Unity Azure| Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: E11DA08B-7341-4743-A817-0CAD59844305
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 472b6d5adae5e23007b9c1aa4d9c75118a94e1cc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="heatmapscene-explanation"></a>Explication de HeatmapScene

HeatmapScene contient une instance du préfabriqué **LevelGeometry**. Ainsi, les coordonnées des incidents chargées à partir d’Azure sont correctement mappées à l’illustration du niveau.

## <a name="heatmap-script"></a>Script Heatmap

### <a name="initializecrashlistasync"></a>InitializeCrashListAsync
`InitializeCrashListAsync` se connecte à la table facile CrashInfo sur Azure et utilise <a href="https://msdn.microsoft.com/en-us/library/azure/jj554274(v=azure.10).aspx">`ToListAsync`</a> pour ajouter toutes ses entrées à une liste.

```
private async Task InitializeCrashListAsync()
 {
     Debug.Log("Downloading crash data from Azure...");

     for (int i = 0; i < numberOfAttempts; i++)
     {
         try
         {
             Debug.Log("Connecting... attempt " + (i +1));
             crashesFromServer = await crashesTable.ToListAsync();
             Debug.Log("Done downloading.");
             return;
         }
         catch (System.Exception e)
         {
             Debug.Log("Error connecting: " + e.Message);
         }

         if (i == numberOfAttempts - 1)
             Debug.Log("Connection failed. Check logs, try again later.");
         else
             await Task.Delay(500);
     }
 }
```

### <a name="spawnmarkersfromlist"></a>SpawnMarkersFromList
`SpawnMarkersFromList` effectue une itération dans la liste des incidents reçue à partir d’Azure et instancie un préfabriqué de marqueur d’incident pour chaque entrée.

```csharp
private void SpawnMarkersFromList()
{
    foreach (var item in crashesFromServer)
    {
        GameObject marker = GameObject.Instantiate(markerPrefab);
        marker.transform.position = new Vector3 { x = item.X, y = item.Y, z = item.Z };
    }
}
```

### <a name="deletecrashdataasync"></a>DeleteCrashDataAsync

`DeleteCrashDataAsync` est appelé quand l’utilisateur appuie sur le bouton **Clear Data** (Effacer les données). Il effectue une itération dans la liste locale des incidents et appelle <a href="https://msdn.microsoft.com/en-us/library/azure/jj554258(v=azure.10).aspx">`DeleteAsync`</a> pour chaque entrée. Cela permet d’affecter à la colonne **Deleted** (Supprimé) de chaque entrée dans la table facile la valeur **true**. `ToListAsync` ignore ces entrées supprimées.

```csharp
public async void DeleteCrashDataAsync()
{
    Debug.Log("Deleting crash data...");
    foreach (var item in crashesFromServer)
    {
        try
        {
            await crashesTable.DeleteAsync(item);
        }
        catch (System.Exception e)
        {
            Debug.Log("Error deleting crash data: " + e.Message);
        }
        Debug.Log("Done deleting crash data.");
    }
    SceneManager.LoadScene(SceneManager.GetActiveScene().name);
}
```

## <a name="next-step"></a>Étape suivante

* [Explication de LeaderboardScene](visual-studio-tools-for-unity-azure-leaderboardscene.md)