---
title: Création d’une extension avec une fenêtre outil | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 597b84854dd398abee9dc21090e085273bc94c75
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903888"
---
# <a name="create-an-extension-with-a-tool-window"></a>Créer une extension avec une fenêtre outil

Dans cette procédure, vous allez apprendre à utiliser le modèle de projet VSIX et le modèle d’élément de **fenêtre outil personnalisé** pour créer une extension avec une fenêtre outil.

## <a name="prerequisites"></a>Prérequis

 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-tool-window"></a>Créer une fenêtre outil

1. Créez un projet VSIX nommé **FirstWindow**. Vous pouvez trouver le modèle de projet VSIX dans la boîte de dialogue **nouveau projet** en recherchant « VSIX ».

2. Lorsque le projet s’ouvre, ajoutez un modèle d’élément de fenêtre outil nommé **myWindow**. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et sélectionnez **Ajouter**  >  **un nouvel élément**. Dans la boîte de dialogue **Ajouter un nouvel élément** , accédez à extensibilité **Visual C#**  >  **Extensibility** et sélectionnez **fenêtre outil personnalisée**. Dans le champ **nom** en bas de la fenêtre, remplacez le nom de fichier de la fenêtre outil par *myWindow.cs*.

3. Générez le projet et commencez le débogage.

   L’instance expérimentale de Visual Studio s’affiche. Pour plus d’informations sur l’instance expérimentale, consultez [l’instance expérimentale](../extensibility/the-experimental-instance.md).

4. Dans l’instance expérimentale, accédez à **Afficher**  >  **autres fenêtres**.

   Vous devez voir un élément de menu pour **myWindow**. Cliquez dessus.

   Vous devez voir une fenêtre outil avec le titre **myWindow** et un bouton indiquant **Click Me !.**
