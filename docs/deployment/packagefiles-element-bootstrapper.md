---
title: '&lt;Tâches PackageFiles&gt; élément (programme d’amorçage) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <PackageFiles> element [bootstrapper]
ms.assetid: 3ea252d7-18a3-47d8-af83-47feebcfe82b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fd2436f7aa3fe24e90f380cf523b3affa6579e2b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990345"
---
# <a name="ltpackagefilesgt-element-bootstrapper"></a>&lt;Tâches PackageFiles&gt; élément (programme d’amorçage)
Le `PackageFiles` élément contient `PackageFile` éléments qui définissent les packages d’installation exécutées en raison de la `Command` élément.  

## <a name="syntax"></a>Syntaxe  

```xml  
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
|`CopyAllPackageFiles`|Optionnel. Si la valeur `false`, le programme d’installation téléchargera uniquement les fichiers référencés à partir du `Command` élément. Si la valeur `true`, tous les fichiers seront téléchargés.<br /><br /> Si la valeur `IfNotHomesite`, le programme d’installation se comportera comme si `False` si `ComponentsLocation` a la valeur `HomeSite`et sinon se comporte comme si `True`. Ce paramètre peut être utile pour permettre aux packages qui sont eux-mêmes des programmes d’amorçage exécuter leur propre comportement dans un scénario HomeSite.<br /><br /> La valeur par défaut est `true`.|  

## <a name="packagefile"></a>PackageFile  
 Le `PackageFile` élément est un enfant de le `PackageFiles` élément. Un `PackageFiles` élément doit avoir au moins un `PackageFile` élément.  

 `PackageFile` a les attributs suivants.  


| Attribut | Description |
|---------------| - |
| `Name` | Obligatoire. Le nom du fichier du package. Il s’agit du nom qui le `Command` élément référence lorsqu’il définit les conditions d’installation d’un package. Cette valeur est également utilisée comme clé dans le `Strings` table pour récupérer le nom localisé des outils tels que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour décrire le package. |
| `HomeSite` | Optionnel. L’emplacement du package sur le serveur distant, si elle n’est pas inclus dans le programme d’installation. |
| `CopyOnBuild` | Optionnel. Spécifie si le programme d’amorçage doit copier le fichier de package sur le disque au moment de la génération. La valeur par défaut est true. |
| `PublicKey` | La clé publique chiffrée du signataire de certificat du package. Obligatoire si `HomeSite` est utilisée ; sinon, facultatif. |
| `Hash` | Optionnel. Un hachage SHA1 du fichier du package. Cela est utilisé pour vérifier l’intégrité du fichier au moment de l’installation. Si le hachage identique ne peut pas être calculé à partir du fichier de package, le package ne sera pas installé. |

## <a name="example"></a>Exemple  
 L’exemple de code suivant définit des packages pour le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] redistributable package et ses dépendances, telles que le programme d’installation de Windows.  

```xml  
<PackageFiles>  
    <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>  
    <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetchk.exe"/>  
</PackageFiles>  
```  

## <a name="see-also"></a>Voir aussi  
 [\<Produit > élément](../deployment/product-element-bootstrapper.md)   
 [\<Package > élément](../deployment/package-element-bootstrapper.md)   
 [Informations de référence sur le schéma de produit et de package](../deployment/product-and-package-schema-reference.md)