---
title: "MSBuild Error MSB3482 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.SignFile.SignToolError"
helpviewer_keywords: 
  - "MSB3482"
ms.assetid: fd09371f-2658-4534-affa-edb485575f1a
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3482
**MSB3482 : Une erreur s’est produite lors de la signature : '\<erreur\>'.**  
  
 Quand vous publiez en utilisant le déploiement ClickOnce ou quand vous utilisez SignTool pour signer des manifestes, cette erreur générée par SignTool peut se produire. Les problèmes courants sont répertoriés ici.  
  
 **Une erreur s’est produite lors de la signature : 'La valeur ne peut pas être null. Nom du paramètre : strongNameKey'.**  
  
 Cette erreur peut s’afficher dans la liste d’erreurs pendant le déploiement de ClickOnce. Le problème provient de la sélection d’une clé de signature non valide. En général, vous essayez d’utiliser une clé qui ne fait pas l’objet d’un chiffrement RSA. SignTool ne prend en charge que le chiffrement de clé RSA.  
  
 Pour corriger cette erreur, obtenez une clé faisant l’objet d’un chiffrement RSA avec activation de la signature de code.  
  
 **Une erreur s’est produite lors de la signature : 'Une chaîne de certificats n’a pas pu être établie vers une autorité racine de confiance.'**  
  
 Cette erreur peut s’afficher dans la liste d’erreurs pendant le déploiement de ClickOnce. Le problème est dû au fait que la chaîne ou l’autorité racine du certificat n’est pas approuvée sur l’ordinateur de l’utilisateur. Cela se produit généralement lors du déplacement de certificats\/clés entre ordinateurs.  
  
 Pour corriger cette erreur, installez le « certificat racine » de l’Autorité de certification à l’origine de celui\-ci. En règle générale, vous pouvez accéder au site web du fournisseur de l’autorité de certification et le télécharger à nouveau en cas de besoin.  
  
 **Une erreur s’est produite lors de la signature : 'Échec de la signature... \\setup.exe. Erreur de SignTool : ISignCode::Sign a renvoyé l’erreur : 0x80880253. Le certificat du signataire n’est pas valide pour la signature.'**  
  
 Cette erreur peut s’afficher dans la liste d’erreurs pendant le déploiement de ClickOnce.  
  
 Le problème est probablement dû au fait que le certificat n’est pas inclus dans la plage de dates valides, ce qui peut arriver si votre certificat est arrivé à expiration.  
  
 Pour corriger cette erreur, obtenez un certificat mis à jour avec une date valide.  
  
 Pour plus d’informations sur la mise à jour du certificat, consultez l’article 925521 intitulé « Vous recevez un message d’erreur quand vous essayez mettre à jour une application ClickOnce Visual Studio 2005 après expiration du certificat utilisé pour signer l’installation » dans la Base de connaissances Microsoft à l’adresse [http:\/\/support.microsoft.com](http://support.microsoft.com/kb/925521).  
  
 **Le jeu de clés n’existe pas.**  
  
 Le fichier .pfx et le certificat sont peut\-être incompatibles. Essayez de supprimer et de réinstaller le certificat ou essayez de recréer le fichier .pfx.  
  
 **Clé non valide pour l’utilisation dans l’état spécifié**  
  
 Consultez http:\/\/blogs.msdn.com\/b\/smondal\/archive\/2012\/05\/08\/an\-error\-occurred\-while\-signing\-key\-not\-valid\-for\-use\-in\-specified\-state.aspx  
  
 **Le paramètre est incorrect.**  
  
 Votre build est\-elle en cours d’exécution dans un service ou un compte d’utilisateur autre que celui utilisé pour importer le certificat ? Essayez de désactiver tous les paramètres Stratégie de sécurité locale qui nécessitent une protection de la clé privée.  Ensuite, supprimez et réimportez le certificat pour le compte d’utilisateur de la build.  
  
 **L’opération requise ne peut pas être terminée.  L’ordinateur doit être approuvé pour la délégation et le compte d’utilisateur actuel doit être configuré afin d’autoriser la délégation.**  
  
 Consultez [ce billet de blog MSDN.](http://technet.microsoft.com/en-us/library/cc782684\(v=ws.10\).aspx)  
  
## Voir aussi  
 [Présentation de la signature de code](https://msdn.microsoft.com/en-us/library/ms537361\(v=vs.85\).aspx)   
 [SignTool.exe \(Sign Tool\)](../Topic/SignTool.exe%20\(Sign%20Tool\).md)   
 [Page Signature, Concepteur de projets](../ide/reference/signing-page-project-designer.md)   
 [Comment : signer un assembly \(Visual Studio\)](http://msdn.microsoft.com/fr-fr/f468a7d3-234c-4353-924d-8e0ae5896564)   
 [Comment : signer un assembly avec un nom fort](../Topic/How%20to:%20Sign%20an%20Assembly%20with%20a%20Strong%20Name.md)   
 [Assemblys avec nom fort](../Topic/Strong-Named%20Assemblies.md)   
 [Signature avec nom fort pour les applications gérées](http://msdn.microsoft.com/fr-fr/5fef3490-c519-4363-94fd-8b1ad260dab5)   
 [\<PackageFiles\>, élément](../deployment/packagefiles-element-bootstrapper.md)