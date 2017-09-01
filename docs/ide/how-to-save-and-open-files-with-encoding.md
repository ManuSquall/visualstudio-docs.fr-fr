---
title: Guide pratique pour enregistrer et ouvrir des fichiers avec encodage | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Unicode, bi-directional language support
- files, encoding
- bi-directional language support, encoded files
- file encoding, bi-directional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
caps.latest.revision: 8
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 83faa2ad32073c4133295953afa6259e88eee2d5
ms.contentlocale: fr-fr
ms.lasthandoff: 05/30/2017

---
# <a name="how-to-save-and-open-files-with-encoding"></a>Comment : enregistrer et ouvrir des fichiers avec encodage
Vous pouvez enregistrer des fichiers avec encodage de caractères spécifiques pour prendre en charge des langues bidirectionnelles. Vous pouvez également spécifier un codage à l’ouverture d’un fichier, afin que Visual Studio affiche le fichier correctement.  
  
### <a name="to-save-a-file-with-encoding"></a>Pour enregistrer un fichier avec encodage  
  
1.  Dans le menu **Fichier**, choisissez **Enregistrer le fichier sous**, puis cliquez sur le bouton déroulant à côté du bouton **Enregistrer**.  
  
     La boîte de dialogue **Options d’enregistrement avancées** s’affiche.  
  
2.  Sous **Encodage**, sélectionnez l’encodage à utiliser pour le fichier.  
  
3.  Éventuellement, sous **Fins de ligne**, sélectionnez le format des caractères de fin de ligne.  
  
     Cette option est utile si vous souhaitez échanger le fichier avec des utilisateurs d’un système d’exploitation différent.  
  
     Si vous souhaitez utiliser un fichier qui est codé de manière spécifique, vous pouvez indiquer à Visual Studio d’utiliser cet encodage à l’ouverture du fichier. La méthode que vous utilisez varie selon que le fichier fait ou non partie de votre projet.  
  
### <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>Pour ouvrir un fichier encodé qui fait partie d’un projet  
  
1.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier et choisissez **Ouvrir avec**.  
  
2.  Dans la boîte de dialogue **Ouvrir avec**, choisissez l’éditeur avec lequel vous voulez ouvrir le fichier.  
  
     De nombreux éditeurs Visual Studio, tels que l’éditeur de formulaires, détectent automatiquement l’encodage et ouvrent le fichier de façon appropriée. Si vous optez pour un éditeur qui vous permet de choisir l’encodage, la boîte de dialogue **Encodage** s’affiche.  
  
3.  Dans la boîte de dialogue **Encodage**, sélectionnez le codage que l’éditeur doit utiliser.  
  
### <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>Pour ouvrir un fichier encodé qui ne fait pas partie d’un projet  
  
1.  Dans le menu **Fichier**, pointez sur **Ouvrir**, choisissez **Fichier** ou **Fichier à partir du web**, puis sélectionnez le fichier à ouvrir.  
  
2.  Cliquez sur le bouton déroulant en regard du bouton **Ouvrir**, puis choisissez **Ouvrir avec**.  
  
3.  Suivez les étapes 2 et 3 de la procédure précédente.  
  
## <a name="see-also"></a>Voir aussi  
 [Encodage et globalisation des applications Windows Forms](/dotnet/framework/winforms/advanced/encoding-and-windows-forms-globalization)   
 [Globalisation et localisation d’applications](../ide/globalizing-and-localizing-applications.md)
