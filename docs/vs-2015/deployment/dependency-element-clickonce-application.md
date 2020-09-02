---
title: '&lt;Dependency &gt; , élément (application ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#osVersionInfo
- urn:schemas-microsoft-com:asm.v2#os
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#dependency
- http://www.w3.org/2000/09/xmldsig#DigestValue
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
- urn:schemas-microsoft-com:asm.v2#dependentAssembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], dependency element
- <dependency> element [ClickOnce application manifest]
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
caps.latest.revision: 36
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e79fadcab1a4f00c084d675c3267b5886772fe2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199881"
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;Dependency &gt; , élément (application ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifie une dépendance de plateforme ou d’assembly requise pour l’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      <dependency>  
   <dependentOS  
      supportURL  
      description  
   >  
      <osVersionInfo>  
         <os  
            majorVersion  
            minorVersion  
            buildNumber  
            servicePackMajor  
            servicePackMinor  
            productType  
            suiteType  
         />   
      </osVersionInfo>  
   </dependentOS>  
   <dependentAssembly  
      dependencyType  
      allowDelayedBinding  
      group  
      codeBase  
      size  
   >  
      <assemblyIdentity  
         name  
         version  
         processorArchitecture  
         language  
      >  
         <hash>  
            <dsig:Transforms>  
               <dsig:Transform  
                  Algorithm  
            />  
            </dsig:Transforms>  
            <dsig:DigestMethod />  
            <dsig:DigestValue>  
            </dsig:DigestValue>  
    </hash>  
  
      </assemblyIdentity>  
   </dependentAssembly>  
</dependency>  
```  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 L’élément `dependency` est obligatoire. Il peut y avoir plusieurs instances de `dependency` dans le même manifeste d’application.  
  
 L' `dependency` élément n’a pas d’attributs et contient les éléments enfants suivants.  
  
### <a name="dependentos"></a>avec dépendants  
 facultatif. Contient l' `osVersionInfo` élément. Les `dependentOS` éléments et s’excluent `dependentAssembly` mutuellement : l’un ou l’autre doit exister pour un `dependency` élément, mais pas les deux.  
  
 `dependentOS` prend en charge les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`supportUrl`|facultatif. Spécifie une URL de prise en charge pour la plateforme dépendante. Cette URL est indiquée à l’utilisateur si la plateforme requise est trouvée.|  
|`description`|facultatif. Décrit, dans un format lisible par l’utilisateur, le système d’exploitation décrit par l' `dependentOS` élément.|  
  
### <a name="osversioninfo"></a>osVersionInfo  
 Obligatoire. Cet élément est un enfant de l’élément `dependentOS` et contient l’élément `os` . Cet élément n’a pas d’attributs.  
  
### <a name="os"></a>os  
 Obligatoire. Cet élément est un enfant de l’élément `osVersionInfo` . Cet élément comprend les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`majorVersion`|Obligatoire. Spécifie le numéro de version principale du système d’exploitation.|  
|`minorVersion`|Obligatoire. Spécifie le numéro de version mineure du système d’exploitation.|  
|`buildNumber`|Obligatoire. Spécifie le numéro de build du système d’exploitation.|  
|`servicePackMajor`|Obligatoire. Spécifie le Service Pack numéro principal du système d’exploitation.|  
|`servicePackMinor`|facultatif. Spécifie le Service Pack numéro mineur du système d’exploitation.|  
|`productType`|facultatif. Identifie la valeur du type de produit. Les valeurs correctes sont `server`, `workstation` et `domainController`. Par exemple, pour Windows 2000 professionnel, cette valeur d’attribut est `workstation` .|  
|`suiteType`|facultatif. Identifie une suite de produits disponible sur le système ou le type de configuration du système. Les valeurs valides sont `backoffice`, `blade`, `datacenter`, `enterprise`, `home`, `professional`, `smallbusiness`, `smallbusinessRestricted` et `terminal`. Par exemple, pour Windows 2000 professionnel, cette valeur d’attribut est `professional` .|  
  
### <a name="dependentassembly"></a>dependentAssembly  
 facultatif. Contient l' `assemblyIdentity` élément. Les `dependentOS` éléments et s’excluent `dependentAssembly` mutuellement : l’un ou l’autre doit exister pour un `dependency` élément, mais pas les deux.  
  
 `dependentAssembly` a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`dependencyType`|Obligatoire. Spécifie le type de dépendance. Les valeurs valides sont `preprequisite` et `install`. Un `install` assembly est installé dans le cadre de l' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application. Un `prerequisite` assembly doit être présent dans le global assembly cache (GAC) pour que l' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application puisse être installée.|  
|`allowDelayedBinding`|Obligatoire. Spécifie si l’assembly peut être chargé par programmation au moment de l’exécution.|  
|`group`|facultatif. Si l' `dependencyType` attribut a la valeur `install` , désigne un groupe nommé d’assemblys qui s’installent uniquement à la demande. Pour plus d’informations, consultez [Procédure pas à pas : téléchargement d’assemblys à la demande avec l’API du déploiement ClickOnce à l’aide du concepteur](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md).<br /><br /> Si la valeur `framework` est et que l' `dependencyType` attribut a la valeur `prerequisite` , désigne l’assembly dans le cadre du .NET Framework. Le GAC (global assembly cache) n’est pas vérifié pour cet assembly lors de l’installation de sur [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] et versions ultérieures.|  
|`codeBase`|Obligatoire lorsque l' `dependencyType` attribut a la valeur `install` . Chemin d’accès à l’assembly dépendant. Peut être un chemin d’accès absolu ou un chemin d’accès relatif à la base de code du manifeste. Ce chemin d’accès doit être un URI valide pour que le manifeste d’assembly soit valide.|  
|`size`|Obligatoire lorsque l' `dependencyType` attribut a la valeur `install` . Taille de l’assembly dépendant, en octets.|  
  
### <a name="assemblyidentity"></a>assemblyIdentity  
 Obligatoire. Cet élément est un enfant de l’élément `dependentAssembly` et comprend les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`name`|Obligatoire. Identifie le nom de l’application.|  
|`version`|Obligatoire. Spécifie le numéro de version de l’application au format suivant : `major.minor.build.revision`|  
|`publicKeyToken`|facultatif. Spécifie une chaîne hexadécimale de 16 caractères qui représente les 8 derniers octets de la `SHA-1` valeur de hachage de la clé publique sous laquelle l’application ou l’assembly est signé. La clé publique utilisée pour signer le catalogue doit être de 2048 bits ou plus.|  
|`processorArchitecture`|facultatif. Spécifie le processeur. Les valeurs valides sont `x86` pour les fenêtres 32 bits et `I64` pour Windows 64 bits.|  
|`language`|facultatif. Identifie les codes de langue en deux parties, tels que en-US, de l’assembly.|  
  
### <a name="hash"></a>Hachage  
 L' `hash` élément est un enfant facultatif de l' `assemblyIdentity` élément. L’élément `hash` ne comporte pas d’attributs.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] utilise un hachage algorithmique de tous les fichiers d’une application en tant que vérification de la sécurité, pour s’assurer qu’aucun des fichiers n’a été modifié après le déploiement. Si l' `hash` élément n’est pas inclus, cette vérification ne sera pas effectuée. Par conséquent, l’omission de l' `hash` élément n’est pas recommandée.  
  
### <a name="dsigtransforms"></a>dsig:Transforms  
 L' `dsig:Transforms` élément est un enfant obligatoire de l' `hash` élément. L’élément `dsig:Transforms` ne comporte pas d’attributs.  
  
### <a name="dsigtransform"></a>dsig:Transform  
 L' `dsig:Transform` élément est un enfant obligatoire de l' `dsig:Transforms` élément. L’élément `dsig:Transform` a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Algorithm`|Algorithme utilisé pour calculer le Digest pour ce fichier. Actuellement, la seule valeur utilisée par [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] est `urn:schemas-microsoft-com:HashTransforms.Identity` .|  
  
### <a name="dsigdigestmethod"></a>dsig:DigestMethod  
 L' `dsig:DigestMethod` élément est un enfant obligatoire de l' `hash` élément. L’élément `dsig:DigestMethod` a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Algorithm`|Algorithme utilisé pour calculer le Digest pour ce fichier. Actuellement, la seule valeur utilisée par [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] est `http://www.w3.org/2000/09/xmldsig#sha1` .|  
  
### <a name="dsigdigestvalue"></a>dsig:DigestValue  
 L' `dsig:DigestValue` élément est un enfant obligatoire de l' `hash` élément. L’élément `dsig:DigestValue` ne comporte pas d’attributs. Sa valeur texte est le hachage calculé pour le fichier spécifié.  
  
## <a name="remarks"></a>Notes  
 Tous les assemblys utilisés par votre application doivent avoir un `dependency` élément correspondant. Les assemblys dépendants n’incluent pas les assemblys qui doivent être préinstallés dans le Global Assembly Cache en tant qu’assemblys de plateforme.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre les `dependency` éléments d’un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifeste d’application. Cet exemple de code fait partie d’un exemple plus complet fourni pour la rubrique du [manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md) .  
  
```  
<dependency>  
  <dependentOS>  
    <osVersionInfo>  
      <os   
        majorVersion="4"   
        minorVersion="10"   
        buildNumber="0"   
        servicePackMajor="0" />  
    </osVersionInfo>  
  </dependentOS>  
</dependency>  
<dependency>  
  <dependentAssembly  
    dependencyType="preRequisite"  
    allowDelayedBinding="true">  
    <assemblyIdentity  
      name="Microsoft.Windows.CommonLanguageRuntime"  
      version="4.0.20506.0" />  
  </dependentAssembly>  
</dependency>  
  
<dependency>  
  <dependentAssembly  
    dependencyType="install"  
    allowDelayedBinding="true"  
    codebase="MyApplication.exe"  
    size="4096">  
    <assemblyIdentity  
      name="MyApplication"  
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<dependency> Appartient](../deployment/dependency-element-clickonce-deployment.md)
