---
title: "&lt;dependency&gt; Element (ClickOnce Deployment) | Microsoft Docs"
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
  - "<dependency> element [ClickOnce deployment manifest]"
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 27
---
# &lt;dependency&gt; Element (ClickOnce Deployment)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifie la version de l'application à installer et l'emplacement du manifeste d'application.  
  
## Syntaxe  
  
```  
  
      <dependency>   
   <dependentAssembly  
      preRequisite  
      visible  
      dependencyType  
      codeBase  
      size  
   >   
      <assemblyIdentity   
         name   
         version   
         publicKeyToken   
         processorArchitecture   
         language  
         type  
      />   
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
  
   </dependentAssembly>   
</dependency>  
```  
  
## Éléments et attributs  
 L'élément `dependency` est obligatoire.  Il ne possède aucun attribut.  Un manifeste de déploiement peut avoir plusieurs éléments `dependency`.  
  
 L'élément `dependency` décrit habituellement des dépendances de l'application principale avec des assemblys contenus dans une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Si votre application Main.exe utilise un assembly appelé DotNetAssembly.dll, ce dernier doit être répertorié dans une section de dépendance.  Toutefois, la dépendance peut exprimer également d'autres types de dépendances, par exemple des dépendances avec une version spécifique du Common Language Runtime, avec un assembly du Global Assembly Cache \(GAC\) ou avec un objet COM.  Dans la mesure où il s'agit d'une technologie de déploiement No\-Touch, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ne peut initialiser le téléchargement et l'installation de ces types de dépendances, mais il empêche l'application de s'exécuter si une ou plusieurs des dépendances spécifiées n'existent pas.  
  
## dependentAssembly  
 Obligatoire.  Cet élément contient l'élément `assemblyIdentity`.  Le tableau suivant répertorie les attributs pris en charge par `dependentAssembly`.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`preRequisite`|Facultatif.  Spécifie que cet assembly doit déjà exister dans le GAC.  Les valeurs valides sont `true` et `false`.  Si la valeur est `true` et que l'assembly spécifié n'existe pas dans le GAC, l'application ne peut pas s'exécuter.|  
|`visible`|Facultatif.  Identifie l'identité de l'application de niveau supérieur, y compris ses dépendances.  Utilisé en interne par [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pour gérer l'activation et le stockage d'application.|  
|`dependencyType`|Obligatoire.  Relation entre cette dépendance et l'application.  Les valeurs valides sont :<br /><br /> -   `install`.  Le composant représente une installation séparée de l'application actuelle.<br />-   `preRequisite`.  Le composant est requis par l'application actuelle.|  
|`codebase`|Facultatif.  Chemin d'accès complet au manifeste d'application.|  
|`size`|Facultatif.  Taille du manifeste d'application, en octets.|  
  
## assemblyIdentity  
 Obligatoire.  Cet élément est un enfant de l'élément `dependentAssembly`.  Le contenu de `assemblyIdentity` doit être identique à ce qui est décrit dans le manifeste d'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Le tableau suivant présente les attributs de l'élément `assemblyIdentity`.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Name`|Obligatoire.  Identifie le nom de l'application.|  
|`Version`|Obligatoire.  Spécifie le numéro de version de l'application, au format suivant : `major.minor.build.revision`|  
|`publicKeyToken`|Obligatoire.  Spécifie une chaîne hexadécimale de 16 caractères qui représente les 8 derniers octets de la valeur de hachage SHA\-1 de la clé publique sous laquelle l'application ou l'assembly est signé.  La clé publique utilisée pour la signature doit être une clé de 2048 bits ou plus.|  
|`processorArchitecture`|Obligatoire.  Spécifie le microprocesseur.  Les valeurs valides sont `x86` pour Windows 32 bits et `IA64` pour Windows 64 bits.|  
|`Language`|Facultatif.  Identifie le code de langue en deux parties de l'assembly.  Par exemple, fr\-FR qui représente le français de France.  La valeur par défaut est `neutre`.  Cet élément figure dans l'espace de noms `asmv2`.|  
|`type`|Facultatif.  Pour la compatibilité descendante avec la technologie d'installation côte à côte Windows.  La seule valeur autorisée est `win32`.|  
  
## hash  
 L'élément `hash` est un enfant facultatif de l'élément `file`.  L'élément `hash` ne contient pas d'attributs.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utilise un hachage algorithmique de tous les fichiers dans une application comme vérification de la sécurité, pour garantir qu'aucun des fichiers n'a été modifié après le déploiement.  Si l'élément `hash` n'est pas inclus, cette vérification ne sera pas effectuée. Par conséquent, il n'est pas recommandé d'omettre l'élément `hash`.  
  
## dsig:Transforms  
 L'élément `dsig:Transforms` est un enfant requis de l'élément `hash`.  L'élément `dsig:Transforms` ne contient pas d'attributs.  
  
## dsig:Transform  
 L'élément `dsig:Transform` est un enfant requis de l'élément `dsig:Transforms`.  Le tableau suivant présente les attributs de l'élément `dsig:Transform`.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Algorithm`|Algorithme utilisé pour calculer le Digest de ce fichier.  À l'heure actuelle, la seule valeur utilisée par [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
## dsig:DigestMethod  
 L'élément `dsig:DigestMethod` est un enfant requis de l'élément `hash`.  Le tableau suivant présente les attributs de l'élément `dsig:DigestMethod`.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Algorithm`|Algorithme utilisé pour calculer le Digest de ce fichier.  À l'heure actuelle, la seule valeur utilisée par [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est `http://www.w3.org/2000/09/xmldsig#sha1 #sha1`.|  
  
## dsig:DigestValue  
 L'élément `dsig:DigestValue` est un enfant requis de l'élément `hash`.  L'élément `dsig:DigestValue` ne contient pas d'attributs.  Sa valeur texte est le hachage calculé pour le fichier spécifié.  
  
## Notes  
 Dans les manifestes de déploiement, un élément `assemblyIdentity` unique identifie généralement le nom et la version du manifeste d'application.  
  
## Exemple  
 L'exemple de code suivant illustre un élément `dependency` dans un manifeste de déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
```  
<!-- Identify the assembly dependencies -->  
<dependency>  
  <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="16384">  
    <assemblyIdentity name="MyApplication" version="0.0.0.0" cultural="neutral" processorArchitecture="msil" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
       <dsig:DigestValue>YzXYZJAvj9pgAG3y8jXUjC7AtHg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## Exemple  
 L'exemple de code suivant spécifie une dépendance avec un assembly déjà installé dans le GAC.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />  
  </dependentAssembly>  
</dependency>  
```  
  
## Exemple  
 L'exemple de code suivant spécifie une dépendance avec une version spécifique du Common Language Runtime.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />  
  </dependentAssembly>  
</dependency>  
```  
  
## Exemple  
 L'exemple de code suivant spécifie une dépendance de système d'exploitation.  
  
```  
<dependency>  
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">  
      <osVersionInfo>  
         <os majorVersion="4" minorVersion="10" />  
      </osVersionInfo>  
   </dependentOS>  
</dependency>  
```  
  
## Voir aussi  
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)   
 [\<dependency\> Element](../deployment/dependency-element-clickonce-application.md)