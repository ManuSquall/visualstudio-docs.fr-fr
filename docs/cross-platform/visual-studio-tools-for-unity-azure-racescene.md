---
title: "Procédure pas à pas de RaceScene Visual Studio Tools pour Unity Azure| Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1F9304E8-0F1B-4325-8BED-FE3EB0ADCE8D
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 304fb69ab6e5da058cd3d2a4d6de202fa042b8f9
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="racescene-explanation"></a>Explication de RaceScene

RaceScene utilise [Standard Assets](https://www.assetstore.unity3d.com/en/#!/content/32351) (Ressources standard) d’Unity pour composer le jeu de course de base et le niveau. Dans cette section, les GameObjects appropriés et leurs scripts sont décrits dans l’ordre de leur apparition dans la hiérarchie RaceScene, comme illustré dans la capture d’écran ci-dessous.

![RaceScene](media/vstu_azure-racescene-explanation-image1.png)

## <a name="multipurposecamerarig"></a>MultipurposeCameraRig

**MultipurposeCameraRig** provient du package de ressources standard **Cameras**. Ses propriétés d’inspection ont été paramétrées pour suivre la voiture à une vitesse appropriée.

## <a name="levelgeometry"></a>LevelGeometry

Le préfabriqué LevelGeometry est un GameObject vide utilisé pour l’organisation. Ses GameObjects enfants constituent l’espace du jeu. Les sols, murs, rampes et obstacles sont tous générés à partir de préfabriqués dans le package de ressources standard **Prototyping**.

**Remarque importante** Pour qu’un objet soit testé par rapport à des incidents enregistrés dans Azure, la balise **Wall** (Mur) doit lui être appliquée.

![RaceScene](media/vstu_azure-racescene-explanation-image2.png)

## <a name="car"></a>Car

Le préfabriqué **Car** provient du package de ressources standard **Vehicles**. La seule modification est que le composant de script **RecordCrashInfo** est ajouté.

### <a name="recordcrashinfo"></a>RecordCrashInfo

Ce script recherche les incidents dans `OnCollisionEnter` et les enregistre dans une liste. `crashRecordingCooldown` et `crashRecordingMinVelocity` limitent ce que le jeu considère comme un incident afin de conserver un jeu de données pertinentes.

Quand l’événement `RaceFinished` est déclenché, `UploadNewCrashDataAsync` envoie chaque incident de la liste à la table facile CrashInfo sur Azure.

```Csharp
using System.Collections;
using System.Collections.Generic;
using System.Threading.Tasks;
using UnityEngine;

public class RecordCrashInfo : MonoBehaviour
{
    [Tooltip("Time in seconds after a crash before a new crash can be recorded.")]
    [SerializeField]
    private float crashRecordingCooldown = 1;

    [Tooltip("How fast car must be traveling before crash can be recorded.")]
    [SerializeField]
    private float crashRecordingMinVelocity = 8;

    [SerializeField]
    private Rigidbody carRigidbody;

    [SerializeField]
    private GameObject crashMarkerPrefab;

    [Tooltip("If turned on, crash markers spawn when the player crashes.")]
    [SerializeField]
    private bool spawnDebugMarkers = false;

    private bool isOnCooldown = false;
    private bool meetsMinVelocity = false;
    private bool isRaceFinished = false;

    private List<CrashInfo> newCrashes = new List<CrashInfo>();

    private void LateUpdate()
    {
        // We have to update this in LateUpdate as opposed to checking in OnCollisionEnter.
        // The car's velocity has already decreased from crashing by the time
        // OnCollisionEnter gets called.

        meetsMinVelocity = carRigidbody.velocity.magnitude >= crashRecordingMinVelocity;
    }

    private void OnCollisionEnter(Collision collision)
    {
        if (!isRaceFinished && collision.gameObject.tag == "Wall" && !isOnCooldown && meetsMinVelocity)
        {
            Debug.Log("Collided with wall!");

            newCrashes.Add(new CrashInfo
            {
                X = collision.transform.position.x,
                Y = collision.transform.position.y,
                Z = collision.transform.position.z
            });

            if (spawnDebugMarkers && Debug.isDebugBuild)
                Instantiate(crashMarkerPrefab, collision.transform.position, Quaternion.identity);

            isOnCooldown = true;
            StartCoroutine(Cooldown());
        }  
    }

    private IEnumerator Cooldown()
    {
        yield return new WaitForSeconds(crashRecordingCooldown);

        isOnCooldown = false;
    }

    private void OnRaceFinished()
    {
        Task.Run(UploadNewCrashDataAsync);
    }

    private async Task UploadNewCrashDataAsync()
    {
        var crashTable = AzureMobileServiceClient.Client.GetTable<CrashInfo>();

        try
        {
            Debug.Log("Uploading crash data to Azure...");

            foreach (var item in newCrashes)
            {
                await crashTable.InsertAsync(item);
            }
            Debug.Log("Finished uploading crash data.");
        }
        catch (System.Exception e)
        {
            Debug.Log("Error uploading crash data: " + e.Message);
        }

    }

    private void OnEnable()
    {
        Checkpoint.RaceFinished += OnRaceFinished;
    }

    private void OnDisable()
    {
        Checkpoint.RaceFinished -= OnRaceFinished;
    }

}
```

## <a name="checkpoints"></a>checkpoints

Le niveau a quatre GameObjects avec le composant de script **Checkpoint**. Les points de contrôle permettent de garantir que le joueur ne peut pas terminer la course en parcourant la piste dans le mauvais sens. Ils détectent également quand le joueur termine la course. C’est là où l’événement `RaceFinished` est appelé.

## <a name="invisible-collision"></a>Invisible Collision

Les cubes primitifs standard avec leurs composants MeshRenderer désactivés sont utilisés comme collision invisible pour maintenir le joueur dans les limites. En outre, le matériel physique **Bouncy** est appliqué pour garantir que les voitures volantes rebondissent sur les murs invisibles de façon satisfaisante et pour empêcher le joueur de percuter un mur invisible, de glisser dessus et d’atterrir au sommet d’un mur visible.

## <a name="recordhighscore"></a>RecordHighScore

Ce script vérifie si le joueur a obtenu un nouveau score élevé. Le cas échéant, il affiche la zone `enterNamePopup`, ce qui permet au joueur d’entrer son nom et de cliquer sur **Envoyer**.

Une fois qu’un nom de joueur est envoyé, `UploadNewHighScoreAsync` est appelé et le nouveau score élevé est envoyé à la table facile HighScoreInfo sur Azure.

```csharp
using System.Collections;
using System.Collections.Generic;
using Microsoft.WindowsAzure.MobileServices;
using UnityEngine;
using System.Threading.Tasks;
using System;
using System.Linq;
using UnityEngine.UI;

public class RecordHighScore : MonoBehaviour
{
    [SerializeField]
    private InputField nameInputField;

    [SerializeField]
    private CanvasGroup enterNamePopup;

    private List<HighScoreInfo> highScores;
    private string playerName = string.Empty;

    private async void Start()
    {
        ShowEnterNamePopup(false);
        highScores = await Leaderboard.GetTopHighScoresAsync();
    }

    private void ShowEnterNamePopup(bool shouldShow)
    {
        enterNamePopup.alpha = shouldShow ? 1 : 0;
        enterNamePopup.interactable = shouldShow;
    }

    public void SubmitButtonClicked()
    {
        playerName = nameInputField.text;
    }

    private async void OnAfterMostRecentScoreSet(float newScore)
    {
        bool isNewHighScore = CheckForNewHighScore(newScore);

        if (isNewHighScore)
        {
            Debug.Log("New High Score!");
            await GetPlayerNameAsync();
            await UploadNewHighScoreAsync(newScore);
        }
        else
        {
            Debug.Log("No new high score.");
        }
    }

    private async Task GetPlayerNameAsync()
    {
        // Wait a bit before showing the popup.
        // This just helps the player experience feel
        // less jarring.
        await Task.Delay(2000);
        ShowEnterNamePopup(true);

        // Wait until the player enters a name and clicks submit.
        // OnSubmitButtonClicked will set the playerName.
        while (playerName == string.Empty)
        {
            await Task.Delay(100);
        }

        ShowEnterNamePopup(false);
    }

    private bool CheckForNewHighScore(float newScore)
    {
        Debug.Log("Checking for a new high score...");

        bool isHighScoreListFull = highScores.Count >= Leaderboard.SizeOfHighScoreList;
        var lowerScores = highScores.Where(x => x.Time > newScore);

        return lowerScores.Count() > 0 || !isHighScoreListFull;
    }

    private async Task UploadNewHighScoreAsync(float newScore)
    {
        var newHighScoreInfo = new HighScoreInfo { Name = playerName, Time = newScore };

        try
        {
            Debug.Log("Uploading high score data to Azure...");

            await Leaderboard.HighScoreTable.InsertAsync(newHighScoreInfo);

            Debug.Log("Finished uploading high score data.");
        }
        catch (System.Exception e)
        {
            Debug.Log("Error uploading high score data: " + e.Message);
        }
    }

    private void OnEnable()
    {
        LapTimer.AfterMostRecentScoreSet += OnAfterMostRecentScoreSet;
    }

    private void OnDisable()
    {
        LapTimer.AfterMostRecentScoreSet -= OnAfterMostRecentScoreSet;
    }

}
```

## <a name="next-step"></a>Étape suivante

* [Explication de HeatmapScene](visual-studio-tools-for-unity-azure-heatmapscene.md).
