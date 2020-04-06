---
title: Création d’une extension avec une fenêtre d’outils ( Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17f72cf130c5ff0f2d6d03ca8c460aa98ea39111
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739544"
---
# <a name="create-an-extension-with-a-tool-window"></a>Créer une extension avec une fenêtre d’outils

Dans cette procédure, vous apprenez à utiliser le modèle de projet VSIX et le modèle **d’élément de fenêtre d’outil personnalisé** pour créer une extension avec une fenêtre d’outil.

## <a name="prerequisites"></a>Prérequis

 A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-tool-window"></a>Créer une fenêtre d’outil

1. Créez un projet VSIX nommé **FirstWindow**. Vous pouvez trouver le modèle de projet VSIX dans le dialogue **du nouveau projet** en recherchant "vsix".

2. Lorsque le projet s’ouvre, ajoutez un modèle d’élément de fenêtre d’outil nommé **MyWindow**. Dans la **Solution Explorer**, cliquez à droite sur le nœud du projet et sélectionnez **Ajouter** > **un nouvel article**. Dans le dialogue **Add New Item,** rendez-vous sur **Visual C’Extensibility** > **Extensibility** et **sélectionnez Custom Tool Window**. Dans le champ **de nom** au bas de la fenêtre, changer le nom de fichier de fenêtre d’outil pour *MyWindow.cs*.

3. Générez le projet et commencez le débogage.

   L’exemple expérimental de Visual Studio apparaît. Pour plus d’informations sur l’instance expérimentale, voir [L’exemple expérimental](../extensibility/the-experimental-instance.md).

4. Dans le cas expérimental, allez **voir** > **d’autres Fenêtres**.

   Vous devriez voir un élément de menu pour **MyWindow**. Cliquez dessus.

   Vous devriez voir une fenêtre d’outil avec le titre **MyWindow** et un bouton disant **Click Me!.**
