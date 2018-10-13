---
title: 'Comment : trouver quelle DLL votre programme a causé l’arrêt | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 469d4a3f42fc749a0a7a05f4a034bde28332dc57
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49183168"
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Comment : savoir quelle DLL a causé l'arrêt de votre programme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

REMARQUE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Si votre application tombe en panne pendant un appel à une DLL système ou au code de quelqu'un d'autre, vous devez rechercher la DLL active au moment de l'incident. Si vous rencontrez un incident dans une DLL en dehors de votre propre programme, vous pouvez identifier l’emplacement en utilisant le **Modules** fenêtre.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Pour savoir où une panne s'est produite à l'aide de la fenêtre Modules  
  
1.  Notez l'adresse où la panne s'est produite.  
  
2.  Sur le **déboguer** menu, choisissez **Windows**, puis cliquez sur **Modules**.  
  
3.  Dans le **Modules** fenêtre, recherchez le **adresse** colonne. Faites défiler la fenêtre à l'aide de la barre de défilement, si nécessaire.  
  
4.  Cliquez sur le **adresse** bouton en haut de la colonne pour trier les DLL par adresse.  
  
5.  Recherchez dans la liste triée la DLL dont la plage d'adresse contient l'emplacement de la panne.  
  
6.  Examinez le **nom** et **chemin d’accès** colonnes pour afficher le nom de la DLL et le chemin d’accès.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : déboguer des DLL natives](../debugger/how-to-debug-native-dlls.md)   
 [Guide pratique pour utiliser la fenêtre Modules](../debugger/how-to-use-the-modules-window.md)





