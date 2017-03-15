---
title: Signature de Packages VSIX | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: da489f0fd0483cddbefb2899eb91bd1d56735d62
ms.lasthandoff: 02/22/2017

---
# <a name="signing-vsix-packages"></a>Signature de Packages VSIX
Assemblys d’extension ne souhaitez pas être signés avant qu’ils peuvent s’exécuter dans Visual Studio, mais il est conseillé de le faire.  
  
 Si vous souhaitez sécuriser votre extension et assurez-vous qu’il n’a pas été falsifié, vous pouvez ajouter une signature numérique à un package VSIX. Lorsqu’un projet VSIX est signé, le programme d’installation de l’extension VSIX affichera un message indiquant qu’il est signé, ainsi que de plus d’informations sur la signature proprement dite. Si le contenu de l’extension VSIX qui ont été modifié, et cette dernière n’a pas été signée à nouveau, l’installateur VSIX affichera que la signature n’est pas valide. L’installation n’est pas arrêtée, mais l’utilisateur est averti.  
  
> [!IMPORTANT]
>  À compter de 2015, de packages VSIX signés à l’aide d’autre que le chiffrement SHA256 seront identifiés comme ayant une signature non valide. Installation de l’extension VSIX n’est pas bloquée, mais l’utilisateur est averti.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>Signature d’un projet VSIX avec VSIXSignTool  
 Il existe un chiffrement SHA256 outil disponible à partir de la signature [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) sur nuget.org à [VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### <a name="to-use-the-vsixsigntool"></a>Pour utiliser le VSIXSignTool  
  
1.  Ajoutez votre VSIX à un projet.  
  
2.  Cliquez avec le bouton droit sur le nœud du projet dans l’Explorateur de solutions, sélectionnez **ajouter | Gérer les Packages NuGet**.  Pour plus d’informations sur NuGet et ajout de NuGet packages, consultez [vue d’ensemble de NuGet](http://docs.nuget.org/) et [gérer NuGet Packages à l’aide de la boîte de dialogue](http://docs.nuget.org/Consume/Package-Manager-Dialog).  
  
3.  Recherchez VSIXSignTool de VisualStudioExtensibility et installez le package NuGet.  
  
4.  Vous pouvez maintenant exécuter le VSIXSignTool à partir de l’emplacement du projet lots locaux. Consultez l’aide de l’outil ligne de commande pour votre scénario de signature (VSIXSignTool.exe / ?).  
  
 Par exemple, pour vous connecter avec un mot de passe protégé le fichier de certificat :  
  
 VSIXSignTool.exe connexion /f \<certfile > /p \<mot de passe > \<VSIXfile >  
  
## <a name="see-also"></a>Voir aussi  
 [Envoi des Extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
