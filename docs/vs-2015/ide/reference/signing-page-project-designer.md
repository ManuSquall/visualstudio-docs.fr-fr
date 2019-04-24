---
title: Signature, page du Concepteur de projet | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.AddNewStrongNameKey
- ResolveKeySource.KeyFileForSignAssemblyNotImported
- vb.ProjectPropertiesSigning.ChangePasswordDialog
- ResolveKeySource.KeyFileForManifestNotImported
- vb.ProjectPropertiesSigning
- vb.ProjectPropertiesSigning.PasswordNeededDialog
- vb.ProjectPropertiesSigning.PfxPasswordDialog
helpviewer_keywords:
- Project Designer, Signing page
- Signing page in Project Designer
ms.assetid: dab3ba13-2f92-4827-92bd-1be3c35bc48b
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 01bfaf5ee9143a3122f779ab8292210b90da771f
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59650394"
---
# <a name="signing-page-project-designer"></a>Page Signature, Concepteur de projets
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Utilisez la page **Signature** du **Concepteur de projet** pour signer les manifestes d’application et de déploiement, et pour signer l’assembly (signature avec nom fort).  
  
 Notez que la signature des manifestes d’application et de déploiement est un processus différent de la signature des assemblys, même si ces deux tâches sont effectuées dans la page **Signature**.  
  
 De plus, le stockage des informations de fichier de clé n’est pas le même pour la signature de manifestes et pour la signature d’assemblys. Pour la signature de manifestes, les informations de clé sont stockées dans la base de données de stockage de chiffrement de votre ordinateur, ainsi que dans le magasin de certificats Windows de l’utilisateur actuel. Pour la signature d’assemblys, les informations de clé sont stockées uniquement dans la base de données de stockage de chiffrement de votre ordinateur.  
  
 Pour accéder à la boîte de dialogue **Signature**, sélectionnez un nœud de projet dans l’**Explorateur de solutions**, puis cliquez sur **Propriétés** dans le menu **Projet**. Lorsque le **Concepteur de projet** apparaît, cliquez sur l’onglet **Signature**.  
  
## <a name="application-and-deployment-manifest-signing"></a>Signature de manifestes d’application et de déploiement  
 Case à cocher **Signer les manifestes ClickOnce**  
 Cochez cette case pour signer les manifestes d’application et de déploiement à l’aide d’une paire de clés publique/privée. Pour plus d’informations sur la manière de procéder, consultez [Guide pratique pour signer des manifestes d’application et de déploiement](../../ide/how-to-sign-application-and-deployment-manifests.md).  
  
 Bouton **Sélectionner dans Store**  
 Permet de sélectionner un certificat existant à partir du magasin de certificats personnel de l’utilisateur actuel. Vous pouvez sélectionner l’un de ces certificats pour signer vos manifestes d’application et de déploiement.  
  
 Quand vous cliquez sur **Sélectionner dans Store**, la boîte de dialogue **Sélectionner un certificat** s’ouvre. Celle-ci répertorie les certificats de votre magasin de certificats personnel qui sont valides (non expirés) et qui ont une clé privée. L’objectif du certificat que vous sélectionnez doit inclure la signature de code.  
  
 Si vous cliquez sur **Afficher les propriétés du certificat**, la boîte de dialogue **Détails du certificat** s’affiche. Cette boîte de dialogue inclut des informations détaillées sur le certificat et des options supplémentaires. Vous pouvez cliquer sur **En savoir plus sur les certificats** pour afficher des informations d’aide supplémentaires.  
  
 Bouton **À partir d’un fichier**  
 Permet de sélectionner un certificat à partir d’un fichier de clé existant.  
  
 Si vous cliquez sur **À partir d’un fichier**, la boîte de dialogue **Sélectionner le fichier** s’ouvre et vous permet de sélectionner un fichier de clé de certificat (.pfx). Le fichier doit être protégé par mot de passe et ne peut pas déjà se trouver dans votre magasin de certificats personnel.  
  
 Dans la boîte de dialogue **Entrez le mot de passe pour ouvrir le fichier**, entrez un mot de passe pour ouvrir le fichier de clé de certificat (.pfx). Les informations de mot de passe sont stockées dans votre liste personnelle de conteneurs de clés et dans votre magasin de certificats personnel.  
  
 Bouton **Créer un certificat de test**  
 Permet de créer un certificat à des fins de test. Le certificat de test est utilisé pour signer vos manifestes d’application et de déploiement ClickOnce.  
  
 Si vous cliquez sur **Créer un certificat de test**, la boîte de dialogue **Créer un certificat de test** s’ouvre. Vous pouvez y taper le mot de passe du fichier de clé de nom fort pour le certificat de test. Le fichier se nomme *nom_projet*_TemporaryKey.pfx. Si vous cliquez sur **OK** sans taper de mot de passe, le fichier .pfx ne sera pas chiffré par mot de passe.  
  
 Boîte de dialogue **URL du serveur d’horodatage**  
 Spécifie l’adresse d’un serveur qui horodate votre signature. Quand vous fournissez un certificat, ce site externe vérifie l’heure à laquelle l’application a été signée.  
  
## <a name="assembly-signing"></a>Signature d’assemblys  
 Case à cocher **Signer l’assembly**.  
 Cochez cette case pour signer l’assembly et créer un fichier de clé de nom fort. Pour plus d’informations sur la signature d’assemblys à l’aide du **Concepteur de projet**, consultez [Guide pratique pour signer un assembly (Visual Studio)](http://msdn.microsoft.com/f468a7d3-234c-4353-924d-8e0ae5896564).  
  
 Cette option utilise l’outil Al.exe fourni par le [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)] pour signer l’assembly. Pour plus d’informations sur Al.exe, consultez [Guide pratique pour signer un assembly avec un nom fort](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).  
  
 Liste **Choisir un fichier de clé de nom fort**  
 Permet de spécifier un fichier de clé de nom fort nouveau ou existant pour signer l’assembly. Sélectionnez **\<Parcourir...>** pour sélectionner un fichier de clé existant.  
  
 Sélectionnez **\<Nouveau...>** pour créer un fichier de clé avec lequel signer l’assembly. La boîte de dialogue **Créer une clé de nom fort** s’ouvre. Vous pouvez l’utiliser pour spécifier un nom de fichier de clé et pour protéger le fichier de clé avec un mot de passe. Le mot de passe doit comporter au moins 6 caractères. Si vous spécifiez un mot de passe, un fichier d’échange d’informations personnelles (.pfx) est créé. Si vous ne spécifiez pas de mot de passe, un fichier de clé de nom fort (.snk) est créé.  
  
 Bouton **Modifier le mot de passe**  
 Modifie le mot de passe du fichier de clé d’échange d’informations personnelles (.pfx) qui est utilisé pour signer l’assembly.  
  
 Quand vous cliquez sur **Modifier le mot de passe**, la boîte de dialogue **Modifier le mot de passe de la clé** s’ouvre. Dans cette boîte de dialogue, l’**ancien mot de passe** correspond au mot de passe actuel du fichier de clé. Le **nouveau mot de passe** doit comporter au moins 6 caractères. Les informations de mot de passe sont stockées dans le magasin de certificats Windows de l’utilisateur actuel.  
  
 Case à cocher **Différer la signature uniquement**  
 Cochez cette case pour différer la signature.  
  
 Notez qu’un projet à signature différée ne s’exécute pas et ne peut pas être débogué. Toutefois, vous pouvez utiliser [Sn.exe (Strong Name Tool)](http://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6) avec l’option `-Vr` pour ignorer l’étape de vérification pendant le développement.  
  
> [!NOTE]
>  Lorsque vous signez un assembly, vous pouvez ne pas avoir accès à une clé privée. Par exemple, une entreprise peut avoir une paire de clés protégées auxquelles les développeurs n’ont pas accès tous les jours. La clé publique peut être disponible, mais l’accès à la clé privée est limité à quelques personnes. Dans ce cas, vous pouvez utiliser la *signature différée* ou la *signature partielle* pour fournir la clé publique, en différant l’ajout de la clé privée jusqu’à ce que l’assembly soit remis.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les propriétés de projet](../../ide/reference/project-properties-reference.md)   
 [Gestion d’assembly et signature de manifeste](../../ide/managing-assembly-and-manifest-signing.md)   
 [Signature avec nom fort pour les applications managées](http://msdn.microsoft.com/5fef3490-c519-4363-94fd-8b1ad260dab5)   
 [Guide pratique pour Application de connexion et les manifestes de déploiement](../../ide/how-to-sign-application-and-deployment-manifests.md)   
 [Guide pratique pour Signer un Assembly (Visual Studio)](http://msdn.microsoft.com/f468a7d3-234c-4353-924d-8e0ae5896564)   
 [Guide pratique pour Signer un Assembly avec un nom fort](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67)   
 [Assemblys avec nom fort](http://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)
