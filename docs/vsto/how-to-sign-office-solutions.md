---
title: "Comment : signer des Solutions Office | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 2883f75c6ca75e1875621f9c6779db09722d6945
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-sign-office-solutions"></a>Comment : signer des solutions Office
  Si vous vous connectez à une solution, vous pouvez accorder une confiance à la solution en utilisant le certificat en tant que preuve. Vous pouvez utiliser le même certificat pour plusieurs solutions, et toutes les solutions seront approuvées avec aucune mise à jour de stratégie de sécurité supplémentaire.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Si vous modifiez manuellement l’application et les manifestes de déploiement à l’aide de la Manifest Generation and Editing Tool (mage.exe et mageui.exe), vous devez signer à nouveau les manifestes avant de pouvoir les utiliser. Pour plus d'informations, consultez [Comment : signer de nouveau des manifestes d'application et de déploiement](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests).  
  
## <a name="signing-by-using-a-certificate"></a>À l’aide d’un certificat de signature  
 Un certificat est un fichier qui contient une clé unique et l’identité de l’éditeur de solutions. Vous pouvez acheter des certificats à partir d’une autorité de certification, ou créer votre propre certificat et une autorité de certification signez-le.  
  
 Visual Studio signe des solutions Office avec un certificat temporaire pour activer le débogage. Vous ne devez pas utiliser le certificat temporaire dans des solutions déployées en tant que preuve.  
  
#### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Pour signer une solution Office à l’aide d’un certificat  
  
1.  Sur le **projet** menu, cliquez sur *SolutionName***propriétés**.  
  
2.  Cliquez sur l’onglet **Signature**.  
  
3.  Sélectionnez **signer les manifestes ClickOnce**.  
  
4.  Recherchez le certificat en cliquant sur **à partir du magasin** ou **sélectionner à partir du fichier** et accéder au certificat.  
  
5.  Pour vérifier que le certificat approprié est utilisé, cliquez sur **plus de détails** pour afficher les informations de certificat.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisation des Solutions Office](../vsto/securing-office-solutions.md)   
 [Accorder la confiance à des Solutions Office](../vsto/granting-trust-to-office-solutions.md)   
 [Page Signature, Concepteur de projet](/visualstudio/ide/reference/signing-page-project-designer)  
  
  