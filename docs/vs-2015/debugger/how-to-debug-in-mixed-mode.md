---
title: 'Comment : déboguer en mode mixte | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c5e2dd4ea0000eefdbd9f74c8fa97c4c63e06fab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681140"
---
# <a name="how-to-debug-in-mixed-mode"></a>Comment : déboguer en mode mixte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les procédures suivantes décrivent comment déboguer le code managé et le code natif, également connu sous le nom de débogage en mode mixte. Pour ce faire, il existe deux scénarios, selon si la DLL ou l'application est écrite en code natif :  
  
- L'application appelante qui appelle votre DLL est écrite en code natif. Dans ce cas, votre DLL est managée et les débogueurs managés et natifs doivent être activés pour déboguer ces deux types de code. Vous pouvez le vérifier dans la boîte de dialogue ** \<Project> pages de propriétés** . Tout dépend si vous avez démarré le débogage à partir du projet DLL ou du projet de l'application appelante.  
  
- L'application appelante qui appelle votre DLL est écrite en code managé et votre DLL est écrite en code natif.  
  
> [!NOTE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l'Aide selon les paramètres actifs ou le mode d'édition. Pour modifier vos paramètres, choisissez **Paramètres d'importation et d'exportation** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-enable-mixed-mode-debugging"></a>Pour activer le débogage en mode mixte  
  
1. Dans **Explorateur de solutions**, sélectionnez le projet.  
  
2. Dans le menu **Affichage**, cliquez sur **Pages de propriétés**.  
  
3. Dans la boîte de dialogue ** \<Project> pages de propriétés** , développez le nœud **Propriétés de configuration** , puis sélectionnez **débogage**.  
  
4. Définissez **Type de débogueur** sur **Mixte** ou **Automatique**.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : déboguer à partir d’un projet DLL](../debugger/how-to-debug-from-a-dll-project.md)
