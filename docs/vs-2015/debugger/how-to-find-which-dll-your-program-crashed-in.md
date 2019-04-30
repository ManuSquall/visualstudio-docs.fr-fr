---
title: 'Procédure : Trouver quelle DLL votre programme a causé l’arrêt | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.dll
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 33e59a2109e408a290ab8b05a5fd8208c7bd1853
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438253"
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Procédure : Trouver quelle DLL votre programme a causé l’arrêt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

REMARQUE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Si votre application tombe en panne pendant un appel à une DLL système ou au code de quelqu'un d'autre, vous devez rechercher la DLL active au moment de l'incident. Si une panne survient dans une DLL en dehors de votre programme, vous pouvez identifier l’emplacement en utilisant la fenêtre **Modules**.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Pour savoir où une panne s'est produite à l'aide de la fenêtre Modules  
  
1. Notez l'adresse où la panne s'est produite.  
  
2. Dans le menu **Déboguer**, sélectionnez **Fenêtres**, puis cliquez sur **Modules**.  
  
3. Dans la fenêtre **Modules**, trouvez la colonne **Adresse**. Faites défiler la fenêtre à l'aide de la barre de défilement, si nécessaire.  
  
4. Cliquez sur le bouton **Adresse** en haut de la colonne pour trier les DLL par adresse.  
  
5. Recherchez dans la liste triée la DLL dont la plage d'adresse contient l'emplacement de la panne.  
  
6. Les colonnes **Nom** et **Chemin d’accès** vous indiquent le nom et le chemin de la DLL.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Déboguer des DLL natives](../debugger/how-to-debug-native-dlls.md)   
 [Guide pratique pour utiliser la fenêtre Modules](../debugger/how-to-use-the-modules-window.md)
