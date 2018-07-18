---
title: 'Comment : signer des solutions Office'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d5fa4a837de66a39502e2c9e2d8466f3998acc4d
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34262189"
---
# <a name="how-to-sign-office-solutions"></a>Comment : signer des solutions Office
  Si vous vous connectez à une solution, vous pouvez accorder une confiance à la solution en utilisant le certificat en tant que preuve. Vous pouvez utiliser le même certificat pour plusieurs solutions, et toutes les solutions seront approuvées avec aucune mise à jour de stratégie de sécurité supplémentaire.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Si vous modifiez manuellement l’application et les manifestes de déploiement à l’aide de la Manifest Generation and Editing Tool (*mage.exe* et *mageui.exe*), vous devez signer à nouveau les manifestes avant de pouvoir les utiliser. Pour plus d’informations, consultez [Comment : signer de nouveau les manifestes de déploiement et d’application](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests).  
  
## <a name="sign-by-using-a-certificate"></a>Se connecter à l’aide d’un certificat  
 Un certificat est un fichier qui contient une clé unique et l’identité de l’éditeur de solutions. Vous pouvez acheter des certificats à partir d’une autorité de certification, ou créer votre propre certificat et une autorité de certification signez-le.  
  
 Visual Studio signe des solutions Office avec un certificat temporaire pour activer le débogage. Vous ne devez pas utiliser le certificat temporaire dans des solutions déployées en tant que preuve.  
  
### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Pour signer une solution Office à l’aide d’un certificat  
  
1.  Sur le **projet** menu, cliquez sur * SolutionName ***propriétés**.  
  
2.  Cliquez sur l’onglet **Signature**.  
  
3.  Sélectionnez **signer les manifestes ClickOnce**.  
  
4.  Recherchez le certificat en cliquant sur **à partir du magasin** ou **sélectionner à partir du fichier** et accéder au certificat.  
  
5.  Pour vérifier que le certificat approprié est utilisé, cliquez sur **plus de détails** pour afficher les informations de certificat.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisez les solutions Office](../vsto/securing-office-solutions.md)   
 [Accorder votre confiance à des solutions Office](../vsto/granting-trust-to-office-solutions.md)   
 [Page Signature, Concepteur de projet](/visualstudio/ide/reference/signing-page-project-designer)  
  
  