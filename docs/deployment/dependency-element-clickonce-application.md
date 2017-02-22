---
title: "&lt;dependency&gt; Element (ClickOnce Application) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#osVersionInfo"
  - "urn:schemas-microsoft-com:asm.v2#os"
  - "http://www.w3.org/2000/09/xmldsig#Transform"
  - "urn:schemas-microsoft-com:asm.v2#dependency"
  - "http://www.w3.org/2000/09/xmldsig#DigestValue"
  - "urn:schemas-microsoft-com:asm.v2#assemblyIdentity"
  - "http://www.w3.org/2000/09/xmldsig#DigestMethod"
  - "http://www.w3.org/2000/09/xmldsig#Transforms"
  - "urn:schemas-microsoft-com:asm.v2#hash"
  - "urn:schemas-microsoft-com:asm.v2#dependentAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "manifests [ClickOnce], dependency element"
  - "<dependency> element [ClickOnce application manifest]"
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
caps.latest.revision: 34
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 34
---
# &lt;dependency&gt; Element (ClickOnce Application)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifie une dépendance de plateforme ou d'assembly requise pour l'application.  
  
## Syntaxe  
  
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
  
## Éléments et attributs  
 L'élément `dependency` est obligatoire.  Il peut exister plusieurs instances de `dependency` dans le même manifeste d'application.  
  
 L'élément `dependency` ne possède pas d'attribut et contient les éléments enfants suivants.  
  
### dependentOS  
 Facultatif.  Contient l'élément `osVersionInfo`.  Les éléments `dependentOS` et `dependentAssembly` s'excluent mutuellement : un élément `dependency` peut posséder l'un ou l'autre, mais pas les deux à la fois.  
  
 `dependentOS` prend en charge les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`supportUrl`|Facultatif.  Spécifie une URL de support pour la plateforme dépendante.  Cette URL est montrée à l'utilisateur si la plateforme requise existe.|  
|`description`|Facultatif.  Décrit, dans un format explicite, le système d'exploitation décrit par l'élément `dependentOS`.|  
  
### osVersionInfo  
 Obligatoire.  Cet élément est un enfant de l'élément `dependentOS` et contient l'élément `os`.  Cet élément ne possède pas d'attribut.  
  
### os  
 Obligatoire.  Cet élément est un enfant de l'élément `osVersionInfo`.  Cet élément possède les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`majorVersion`|Obligatoire.  Spécifie le numéro de version majeure du système d'exploitation.|  
|`minorVersion`|Obligatoire.  Spécifie le numéro de version secondaire du système d'exploitation.|  
|`buildNumber`|Obligatoire.  Spécifie le numéro de build du système d'exploitation.|  
|`servicePackMajor`|Obligatoire.  Spécifie le numéro principal de Service Pack du système d'exploitation.|  
|`servicePackMinor`|Facultatif.  Spécifie le numéro secondaire de Service Pack du système d'exploitation.|  
|`productType`|Facultatif.  Identifie la valeur du type de produit.  Les valeurs valides sont `server`, `workstation` et `domainController`.  Par exemple, cette valeur d'attribut est `workstation` pour Windows 2000 Professionnel.|  
|`suiteType`|Facultatif.  Identifie une suite de produits disponible sur le système, ou le type de configuration du système.  Les valeurs valides sont `backoffice`, `blade`, `datacenter`, `enterprise`, `home`, `professional`, `smallbusiness`, `smallbusinessRestricted` et `terminal`.  Par exemple, cette valeur d'attribut est `professional` pour Windows 2000 Professionnel.|  
  
### dependentAssembly  
 Facultatif.  Contient l'élément `assemblyIdentity`.  Les éléments `dependentOS` et `dependentAssembly` s'excluent mutuellement : un élément `dependency` peut posséder l'un ou l'autre, mais pas les deux à la fois.  
  
 `dependentAssembly` possède les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`dependencyType`|Obligatoire.  Spécifie le type de dépendance.  Les valeurs valides sont `preprequisite` et `install`.  Un assembly `install` est installé dans le cadre de l'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Un assembly `prerequisite` doit être présent dans le Global Assembly Cache \(GAC\) avant l'installation de l'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].|  
|`allowDelayedBinding`|Obligatoire.  Spécifie si l'assembly peut être chargé par programmation à l'exécution.|  
|`group`|Facultatif.  Si l'attribut `dependencyType` a la valeur `install`, désigne un groupe nommé d'assemblys qui s'installent uniquement à la demande.  Pour plus d'informations, consultez [Procédure pas à pas : téléchargement d'assemblys à la demande avec l'API du déploiement ClickOnce à l'aide du concepteur](../Topic/Walkthrough:%20Downloading%20Assemblies%20on%20Demand%20with%20the%20ClickOnce%20Deployment%20API%20Using%20the%20Designer.md).<br /><br /> S'il a la valeur `framework` et si l'attribut `dependencyType` a la valeur `prerequisite`, désigne l'assembly faisant partie du .NET Framework.  Le Global Assemby Cache \(GAC\) n'est pas vérifié pour cet assembly lors de l'installation sur [!INCLUDE[net_v40_short](../debugger/includes/net_v40_short_md.md)] et les versions ultérieures.|  
|`codeBase`|Requis lorsque l'attribut `dependencyType` a la valeur `install`.  Chemin d'accès à l'assembly dépendant.  Il doit s'agir d'un chemin d'accès absolu ou relatif à la base de code du manifeste.  Ce chemin d'accès doit être un URI valide pour que le manifeste d'assembly soit valide.|  
|`size`|Requis lorsque l'attribut `dependencyType` a la valeur `install`.  Taille de l'assembly dépendant en octets.|  
  
### assemblyIdentity  
 Obligatoire.  Cet élément est un enfant de l'élément `dependentAssembly` et possède les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`name`|Obligatoire.  Identifie le nom de l'application.|  
|`version`|Obligatoire.  Spécifie le numéro de version de l'application, au format suivant : `major.minor.build.revision`|  
|`publicKeyToken`|Facultatif.  Spécifie une chaîne hexadécimale de 16 caractères qui représente les 8 derniers octets de la valeur de hachage `SHA-1` de la clé publique sous laquelle l'application ou l'assembly est signé.  La clé publique utilisée pour la signature du catalogue doit être une clé de 2048 bits ou plus.|  
|`processorArchitecture`|Facultatif.  Spécifie le processeur.  Les valeurs valides sont `x86` pour Windows 32 bits et `I64` pour Windows 64 bits.|  
|`language`|Facultatif.  Identifie les codes de la langue de l'assembly, en deux parties \(par exemple, fr\-FR\).|  
  
### hash  
 L'élément `hash` est un enfant facultatif de l'élément `assemblyIdentity`.  L'élément `hash` ne contient pas d'attributs.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utilise un hachage algorithmique de tous les fichiers dans une application comme vérification de la sécurité, pour garantir qu'aucun des fichiers n'a été modifié après le déploiement.  Si l'élément `hash` n'est pas inclus, cette vérification ne sera pas effectuée. Par conséquent, il n'est pas recommandé d'omettre l'élément `hash`.  
  
### dsig:Transforms  
 L'élément `dsig:Transforms` est un enfant requis de l'élément `hash`.  L'élément `dsig:Transforms` ne contient pas d'attributs.  
  
### dsig:Transform  
 L'élément `dsig:Transform` est un enfant requis de l'élément `dsig:Transforms`.  L'élément `dsig:Transform` a les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Algorithm`|Algorithme utilisé pour calculer le Digest de ce fichier.  À l'heure actuelle, la seule valeur utilisée par [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
### dsig:DigestMethod  
 L'élément `dsig:DigestMethod` est un enfant requis de l'élément `hash`.  L'élément `dsig:DigestMethod` a les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Algorithm`|Algorithme utilisé pour calculer le Digest de ce fichier.  À l'heure actuelle, la seule valeur utilisée par [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est `http://www.w3.org/2000/09/xmldsig#sha1 #sha1`.|  
  
### dsig:DigestValue  
 L'élément `dsig:DigestValue` est un enfant requis de l'élément `hash`.  L'élément `dsig:DigestValue` ne contient pas d'attributs.  Sa valeur texte est le hachage calculé pour le fichier spécifié.  
  
## Notes  
 Tous les assemblys utilisés par votre application doivent avoir un élément `dependency` correspondant.  Les assemblys dépendants n'incluent pas les assemblys qui doivent être préinstallés dans le Global Assembly Cache en tant qu'assemblys de plateforme.  
  
## Exemple  
 L'exemple de code suivant illustre les éléments `dependency` dans un manifeste d'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Cet exemple de code fait partie d'un exemple plus développé fourni pour la rubrique [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md).  
  
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
  
## Voir aussi  
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)   
 [\<dependency\> Element](../deployment/dependency-element-clickonce-deployment.md)