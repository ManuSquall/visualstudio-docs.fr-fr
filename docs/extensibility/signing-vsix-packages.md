---
title: Signature de Packages VSIX | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ec875e6877b1c3ff1edf38b29c5e72b757021085
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2018
---
# <a name="signing-vsix-packages"></a>Signature de Packages VSIX
Assemblys d’extension n’avez pas besoin d’être connectés avant qu’ils peuvent s’exécuter dans Visual Studio, mais il est conseillé de le faire.  
  
 Si vous souhaitez sécuriser votre extension et assurez-vous qu’il n’a pas été falsifié, vous pouvez ajouter une signature numérique à un package VSIX. Lorsqu’une extension VSIX est signée, le programme d’installation VSIX affichera un message indiquant qu’elle est signée, ainsi que de plus d’informations sur la signature proprement dite. Si le contenu de l’extension VSIX a été modifié et que l’extension VSIX n’a pas été signé à nouveau, le programme d’installation VSIX affichera que la signature n’est pas valide. L’installation n’est pas arrêtée, mais l’utilisateur est averti.  
  
> [!IMPORTANT]
>  À compter de 2015, les packages VSIX signés à l’aide d’une autre que le chiffrement SHA256 seront identifiés comme ayant une signature non valide. Installation de VSIX n’est pas bloquée, mais l’utilisateur est averti.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>Signature d’une extension VSIX avec VSIXSignTool  
 Il existe un chiffrement SHA256 outil disponible à partir de signature [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) sur nuget.org à [VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### <a name="to-use-the-vsixsigntool"></a>Pour utiliser le VSIXSignTool  
  
1.  Ajouter votre VSIX à un projet.  
  
2.  Cliquez avec le bouton droit sur le nœud de projet dans l’Explorateur de solutions, en sélectionnant **ajouter &#124; Gérer les Packages NuGet**.  Pour plus d’informations sur NuGet et l’ajout de voir des packages NuGet, consultez le [documentation de NuGet](/NuGet) et [Package Manager UI](/NuGet/Tools/Package-Manager-UI) rubriques.  
  
3.  Recherchez VSIXSignTool de VisualStudioExtensibility et installez le package NuGet.  
  
4.  Vous pouvez maintenant exécuter le VSIXSignTool à partir de l’emplacement du projet lots locaux. Consultez l’aide de l’outil ligne de commande pour votre scénario de signature (VSIXSignTool.exe / ?).  
  
 Par exemple, pour vous connecter avec un mot de passe protégé le fichier de certificat :  
  
 VSIXSignTool.exe signe /f \<certfile > /p \<mot de passe > \<VSIXfile >  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md)