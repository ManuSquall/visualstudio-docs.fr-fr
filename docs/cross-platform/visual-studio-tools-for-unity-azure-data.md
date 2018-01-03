---
title: "Procédure pas à pas du modèle de données Visual Studio Tools pour Unity Azure| Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6FCCA8D1-0D06-4B2A-A55F-FC3D1FEA0F56
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 57a6a6aaff1c41a8720f842e20142e3cb1a2e538
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="create-data-model-classes"></a>Créer des classes de modèles de données

Le projet Unity doit contenir des classes de modèles de données qui correspondent aux tables créées dans le back-end Azure Mobile App.

## <a name="create-the-crashinfo-class"></a>Créer la classe CrashInfo

1. Dans Unity, ajoutez un nouveau dossier au répertoire **Assets** (Ressources) racine nommé **Scripts**. Dans le nouveau dossier Scripts, créez un autre dossier nommé **Modèles de données**. Cela concerne uniquement l’organisation.

2. Dans le nouveau dossier Modèles de données, créez un script C# appelé **CrashInfo**.

3. Ouvrez le nouveau script `CrashInfo`, supprimez tout code de modèle, dont la déclaration de classe et les instructions using, puis ajoutez le code suivant :

  ```csharp
  public class CrashInfo
  {
      public string Id { get; set; }
      public float X { get; set; }
      public float Y { get; set; }
      public float Z { get; set; }
  }
  ```

  > [!WARNING]
  > Pour que la procédure pas à pas fonctionne correctement, le nom de la classe du modèle de données doit correspondre au nom de la table facile créée sur le back-end Azure Mobile App.

## <a name="create-the-highscoreinfo-class"></a>Créer la classe HighScoreInfo

1. Dans le dossier Modèles de données, créez un script C# appelé **HighScoreInfo**.

2. Ouvrez le nouveau script `HighScoreInfo`, supprimez tout code de modèle, dont la déclaration de classe et les instructions using, puis ajoutez le code suivant :

  ```csharp
  public class HighScoreInfo
  {
      public string Name { get; set; }
      public float Time { get; set; }
      public string Id { get; set; }
  }
  ```

  ## <a name="next-step"></a>Étape suivante

  * [Implémenter Azure MobileServiceClient](visual-studio-tools-for-unity-azure-mobile-client.md)
