---
title: 'Comment : créer un. Fichier vsct à partir d’un existant. Fichier CTC | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating based on a .ctc file
ms.assetid: 700e80a4-c1e1-4178-af53-45e86dd2c08b
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 7b963436e9d968dd5ba3829e97d0fd0c52e49641
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839541"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Comment : créer un fichier .Vsct à partir d’un fichier .Ctc existant
Vous pouvez créer un fichier .vsct XML à partir d’un fichier source .ctc de table de commande existant. Ainsi, vous pouvez tirer parti du nouveau format du compilateur (VSTC) de table de commande [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] XML.  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Pour créer un fichier .vsct à partir d’un fichier .ctc  
  
1. Obtenez une copie du langage Perl.  
  
2. Obtenez une copie du script perl ConvertCTCToVSCT.pl, généralement situé dans le *\<Visual Studio SDK installation path>* dossier \VisualStudioIntegration\Tools\bin.  
  
3. Obtenez une copie du fichier source .ctc à convertir.  
  
4. Placez les fichiers dans le même répertoire.  
  
5. Dans la fenêtre d’invite de commandes [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , accédez au répertoire.  
  
6. Type  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     où PkgCmd.ctc est le nom du fichier .ctc et PkgCmd.vsct est le nom du fichier .vsct à créer.  
  
     Un nouveau fichier source de table de commande XML .vsct est ainsi créé. Vous pouvez compiler le fichier à l’aide de Vsct.exe, le compilateur VSCT, comme vous le feriez pour tout autre fichier .vsct.  
  
    > [!NOTE]
    > Vous pouvez améliorer la lisibilité du fichier .vsct en reformatant les commentaires XML.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer un. Fichier vsct](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)