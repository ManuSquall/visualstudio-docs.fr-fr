---
title: 'Comment : créer une application console de workflow | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f1334655f2a8b8587922628664e43784b54ce971
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72604915"
---
# <a name="how-to-create-a-workflow-console-application"></a>Procédure : créer une application console de workflow
[!INCLUDE[wf](../includes/wf-md.md)] vous permet de créer des flux de travail pour l’exécution de processus système ou humains. [!INCLUDE[wfd1](../includes/wfd1-md.md)] fournit l'aire de conception pour la création de ces workflows. Le [!INCLUDE[wfd2](../includes/wfd2-md.md)] peut être utilisé pour créer des workflows depuis [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ou il peut être intégré dans d'autres applications pour réhéberger le concepteur.

 Cette rubrique décrit comment utiliser le [!INCLUDE[wfd2](../includes/wfd2-md.md)] dans [!INCLUDE[vs2010](../includes/vs2010-md.md)] pour créer un workflow dans une application console.

### <a name="to-create-a-workflow-console-application"></a>Pour créer une application console de workflow

1. Démarrez [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. Dans le menu **fichier** , pointez sur **nouveau**, puis sélectionnez **projet...**.

     La boîte de dialogue **Nouveau projet** s’affiche.

3. Dans le volet **modèles installés** , sélectionnez **Workflow** dans les regroupements **Visual C#** ou **Visual Basic** , selon le langage de votre choix.

4. Dans le volet central, sélectionnez **application console de workflow**.

5. Dans la zone **nom** , entrez un nom descriptif pour votre projet afin de faciliter son identification.

6. Dans la zone **emplacement** , entrez le répertoire dans lequel vous souhaitez enregistrer votre projet ou cliquez sur **Parcourir** pour y accéder.

7. Dans la zone **solution** , entrez le nom de la nouvelle solution. Cliquez sur **OK** pour créer l’application.

    > [!NOTE]
    > Si vous souhaitez ajouter une application console de workflow à une solution existante, ouvrez cette solution dans [!INCLUDE[vs2010](../includes/vs2010-md.md)] , cliquez avec le bouton droit sur la solution dans **Explorateur de solutions**, puis sélectionnez **Ajouter**, puis **nouveau projet...** pour ouvrir la boîte de dialogue **nouveau projet** . Procédez comme décrit ci-dessus dans cette procédure.

8. Le modèle de projet crée une définition de workflow en XAML et la définition d'application console se trouve dans le code source. [!INCLUDE[wfd2](../includes/wfd2-md.md)] s'ouvre et affiche la zone de dessin du workflow que vous avez créé.

9. Pour composer un workflow, faites glisser des activités ou d’autres éléments de workflow de la **boîte à outils** vers l’aire de conception de votre flux de travail.

## <a name="see-also"></a>Voir aussi
 [Création d'un projet de workflow](../workflow-designer/creating-a-workflow-project.md)