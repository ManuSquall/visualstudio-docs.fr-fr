---
title: '&lt;&gt;Élément PackageFiles (programme d’amorçage) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <PackageFiles> element [bootstrapper]
ms.assetid: 3ea252d7-18a3-47d8-af83-47feebcfe82b
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 382689dada13adce1ee530e66fef6ba78452efaa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188989"
---
# <a name="ltpackagefilesgt-element-bootstrapper"></a>&lt;&gt;Élément PackageFiles (programme d’amorçage)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L' `PackageFiles` élément contient `PackageFile` des éléments qui définissent les packages d’installation exécutés à la suite de l' `Command` élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<PackageFiles  
    CopyAllPackageFiles  
>  
    <PackageFile   
        Name  
        HomeSite  
        CopyOnBuild  
        PublicKey  
        Hash  
    />  
</PackageFiles>  
```  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 L’élément `PackageFiles` comporte l’attribut suivant.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`CopyAllPackageFiles`|facultatif. Si la valeur `false` est, le programme d’installation télécharge uniquement les fichiers référencés à partir de l' `Command` élément. Si la valeur `true` est, tous les fichiers sont téléchargés.<br /><br /> Si la valeur `IfNotHomesite` est, le programme d’installation se comporte de la même façon que si `False` `ComponentsLocation` a la valeur `HomeSite` , et sinon se comporte comme si `True` . Ce paramètre peut être utile pour permettre aux packages qui sont eux-mêmes des programmes d’amorçage d’exécuter leur propre comportement dans un scénario HomeSite.<br /><br /> Par défaut, il s’agit de `true`.|  
  
## <a name="packagefile"></a>PackageFile  
 L' `PackageFile` élément est un enfant de l' `PackageFiles` élément. Un `PackageFiles` élément doit avoir au moins un `PackageFile` élément.  
  
 `PackageFile` a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Name`|Obligatoire. Nom du fichier de package. Il s’agit du nom que l' `Command` élément référencera lorsqu’il définit les conditions d’installation d’un package. Cette valeur est également utilisée comme clé dans la `Strings` table pour récupérer le nom localisé que les outils, tels que, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] utiliseront pour décrire le package.|  
|`HomeSite`|facultatif. Emplacement du package sur le serveur distant, s’il n’est pas inclus dans le programme d’installation.|  
|`CopyOnBuild`|facultatif. Spécifie si le programme d’amorçage doit copier le fichier de package sur le disque au moment de la génération. La valeur par défaut est true.|  
|`PublicKey`|Clé publique chiffrée du signataire du certificat du package. Obligatoire si `HomeSite` est utilisé ; sinon, facultatif.|  
|`Hash`|facultatif. Hachage SHA1 du fichier de package. Cette valeur est utilisée pour vérifier l’intégrité du fichier au moment de l’installation. Si le hachage identique ne peut pas être calculé à partir du fichier de package, le package ne sera pas installé.|  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant définit des packages pour le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] package redistribuable et ses dépendances, tels que le Windows Installer.  
  
```  
<PackageFiles>  
    <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>  
    <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetchk.exe"/>  
</PackageFiles>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [\<Product> Appartient](../deployment/product-element-bootstrapper.md)   
 [\<Package> Appartient](../deployment/package-element-bootstrapper.md)   
 [Référence du schéma de produit et de package](../deployment/product-and-package-schema-reference.md)
