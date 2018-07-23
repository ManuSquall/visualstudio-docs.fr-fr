---
title: '&lt;dépendance&gt; , élément (Application ClickOnce) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1dbd882958c8542be1ec337386634af7dae2e70e
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078558"
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;dépendance&gt; , élément (application ClickOnce)
Identifie une dépendance de plateforme ou l’assembly qui est requise pour l’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
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
 Le `dependency` élément est requis. Il peut y avoir plusieurs instances de `dependency` dans le manifeste d’application.  
  
 Le `dependency` élément n’a pas d’attributs et contient les éléments enfants suivants.  
  
### <a name="dependentos"></a>dependentOS  
 Facultatif. Contient le `osVersionInfo` élément. Le `dependentOS` et `dependentAssembly` éléments s’excluent mutuellement : un ou l’autre doit exister pour un `dependency` élément, mais pas les deux.  
  
 `dependentOS` prend en charge les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`supportUrl`|Facultatif. Spécifie une URL de prise en charge pour la plateforme dépendante. Cette URL est affichée à l’utilisateur si la plateforme nécessaire est trouvée.|  
|`description`|Facultatif. Décrit, dans une forme lisible, le système d’exploitation décrit par le `dependentOS` élément.|  
  
### <a name="osversioninfo"></a>osVersionInfo  
 Obligatoire. Cet élément est un enfant de l’élément `dependentOS` et contient l’élément `os`. Cet élément n’a pas d’attributs.  
  
### <a name="os"></a>système d’exploitation  
 Obligatoire. Cet élément est un enfant de l’élément `osVersionInfo`. Cet élément comprend les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`majorVersion`|Obligatoire. Spécifie le numéro de version principale du système d’exploitation.|  
|`minorVersion`|Obligatoire. Spécifie le numéro de version secondaire du système d’exploitation.|  
|`buildNumber`|Obligatoire. Spécifie le numéro de build du système d’exploitation.|  
|`servicePackMajor`|Obligatoire. Spécifie le numéro majeur de service pack du système d’exploitation.|  
|`servicePackMinor`|Facultatif. Spécifie le numéro secondaire de service pack du système d’exploitation.|  
|`productType`|Facultatif. Identifie la valeur de type de produit. Les valeurs valides sont `server`, `workstation` et `domainController`. Par exemple, pour Windows 2000 Professionnel, cette valeur d’attribut est `workstation`.|  
|`suiteType`|Facultatif. Identifie une suite de produits disponible sur le système, ou le type de configuration du système. Les valeurs valides sont `backoffice`, `blade`, `datacenter`, `enterprise`, `home`, `professional`, `smallbusiness`, `smallbusinessRestricted`, et `terminal`. Par exemple, pour Windows 2000 Professionnel, cette valeur d’attribut est `professional`.|  
  
### <a name="dependentassembly"></a>dependentAssembly  
 Facultatif. Contient le `assemblyIdentity` élément. Le `dependentOS` et `dependentAssembly` éléments s’excluent mutuellement : un ou l’autre doit exister pour un `dependency` élément, mais pas les deux.  
  
 `dependentAssembly` a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`dependencyType`|Obligatoire. Spécifie le type de dépendance. Les valeurs valides sont `preprequisite` et `install`. Un `install` assembly est installé dans le cadre de la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application. Un `prerequisite` assembly doit être présent dans le global assembly cache (GAC) avant le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application peut installer.|  
|`allowDelayedBinding`|Obligatoire. Spécifie si l’assembly peut être chargé par programmation lors de l’exécution.|  
|`group`|Facultatif. Si le `dependencyType` attribut a la valeur `install`, désigne un groupe nommé d’assemblys qui s’installent uniquement à la demande. Pour plus d’informations, consultez [Procédure pas à pas : téléchargement d’assemblys à la demande avec l’API du déploiement ClickOnce à l’aide du concepteur](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md).<br /><br /> Si la valeur `framework` et `dependencyType` attribut a la valeur `prerequisite`, désigne l’assembly dans le cadre du .NET Framework. Le global assembly cache (GAC) n’est pas activé pour cet assembly lors de l’installation sur [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] et versions ultérieures.|  
|`codeBase`|Obligatoire quand le `dependencyType` attribut a la valeur `install`. Le chemin d’accès de l’assembly dépendant. Peut être un chemin d’accès absolu ou un chemin d’accès relatif de code du manifeste base. Ce chemin d’accès doit être un URI valid afin que le manifeste d’assembly soit valide.|  
|`size`|Obligatoire quand le `dependencyType` attribut a la valeur `install`. La taille de l’assembly dépendant, en octets.|  
  
### <a name="assemblyidentity"></a>assemblyIdentity  
 Obligatoire. Cet élément est un enfant de l’élément `dependentAssembly` et comprend les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`name`|Obligatoire. Identifie le nom de l’application.|  
|`version`|Obligatoire. Spécifie le numéro de version de l’application dans le format suivant : `major.minor.build.revision`|  
|`publicKeyToken`|Facultatif. Spécifie une chaîne hexadécimale de 16 caractères qui représente les 8 derniers octets de la `SHA-1` la valeur de la clé publique sous laquelle est signé l’application ou un assembly de hachage. La clé publique utilisée pour signer le catalogue doit être au moins 2 048 bits.|  
|`processorArchitecture`|Facultatif. Spécifie le processeur. Les valeurs valides sont `x86` pour 32 bits Windows et `I64` pour Windows de 64 bits.|  
|`language`|Facultatif. Identifie les codes de langue de deux parties, telles que EN-US, de l’assembly.|  
  
### <a name="hash"></a>hash  
 Le `hash` élément est un enfant facultatif de la `assemblyIdentity` élément. Le `hash` élément ne possède pas d’attributs.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utilise un hachage algorithmique de tous les fichiers dans une application en tant qu’une vérification de sécurité, pour vous assurer qu’aucun des fichiers ont été modifiés après le déploiement. Si le `hash` élément n’est pas inclus, cette vérification ne sera pas effectuée. Par conséquent, en omettant le `hash` élément n’est pas recommandé.  
  
### <a name="dsigtransforms"></a>dsig : TRANSFORMS  
 Le `dsig:Transforms` élément est un enfant requis de le `hash` élément. Le `dsig:Transforms` élément ne possède pas d’attributs.  
  
### <a name="dsigtransform"></a>dsig : Transform  
 Le `dsig:Transform` élément est un enfant requis de le `dsig:Transforms` élément. Le `dsig:Transform` élément a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Algorithm`|L’algorithme utilisé pour calculer le condensat pour ce fichier. La seule valeur utilisée par [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
### <a name="dsigdigestmethod"></a>dsig:DigestMethod  
 Le `dsig:DigestMethod` élément est un enfant requis de le `hash` élément. Le `dsig:DigestMethod` élément a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Algorithm`|L’algorithme utilisé pour calculer le condensat pour ce fichier. La seule valeur utilisée par [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
### <a name="dsigdigestvalue"></a>dsig : DigestValue  
 Le `dsig:DigestValue` élément est un enfant requis de le `hash` élément. Le `dsig:DigestValue` élément ne possède pas d’attributs. Sa valeur de texte est le hachage calculé pour le fichier spécifié.  
  
## <a name="remarks"></a>Notes  
 Tous les assemblys utilisés par votre application doivent correspondre à un `dependency` élément. Assemblys dépendants n’incluent pas les assemblys qui doivent être préinstallés dans le global assembly cache en tant qu’assemblys de plateforme.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre `dependency` éléments dans un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeste d’application. Cet exemple de code fait partie d’un exemple plus complet fourni pour le [manifeste d’Application ClickOnce](../deployment/clickonce-application-manifest.md) rubrique.  
  
```xml  
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
 [\<dépendance > élément](../deployment/dependency-element-clickonce-deployment.md)