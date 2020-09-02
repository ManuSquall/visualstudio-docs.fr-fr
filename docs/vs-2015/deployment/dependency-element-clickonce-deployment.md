---
title: '&lt;Dependency &gt; , élément (déploiement ClickOnce) | Microsoft Docs'
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
- <dependency> element [ClickOnce deployment manifest]
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f191b11dfce5b3877d0a31e260e092000a556a5a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187785"
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;Dependency &gt; , élément (déploiement ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifie la version de l’application à installer et l’emplacement du manifeste de l’application.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 L’élément `dependency` est obligatoire. Elle n’a pas d’attribut. Un manifeste de déploiement peut avoir plusieurs `dependency` éléments.  
  
 L' `dependency` élément exprime généralement les dépendances de l’application principale sur les assemblys contenus dans une [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application. Si votre application Main.exe consomme un assembly appelé DotNetAssembly.dll, cet assembly doit être listé dans une section de dépendance. Toutefois, la dépendance peut également exprimer d’autres types de dépendances, tels que les dépendances sur une version spécifique du common language runtime, sur un assembly dans le Global Assembly Cache (GAC) ou sur un objet COM. Étant donné qu’il s’agit d’une technologie de déploiement sans toucher, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ne peut pas lancer le téléchargement et l’installation de ces types de dépendances, mais elle empêche l’application de s’exécuter si une ou plusieurs des dépendances spécifiées n’existent pas.  
  
## <a name="dependentassembly"></a>dependentAssembly  
 Obligatoire. Cet élément contient l' `assemblyIdentity` élément. Le tableau suivant indique les attributs `dependentAssembly` pris en charge par.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`preRequisite`|facultatif. Spécifie que cet assembly doit déjà exister dans le GAC. Les valeurs valides sont `true` et `false`. Si `true` , et que l’assembly spécifié n’existe pas dans le GAC, l’exécution de l’application échoue.|  
|`visible`|facultatif. Identifie l’identité de l’application de niveau supérieur, y compris ses dépendances. Utilisé en interne par [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] pour gérer le stockage et l’activation des applications.|  
|`dependencyType`|Obligatoire. Relation entre cette dépendance et l’application. Les valeurs autorisées sont :<br /><br /> -   `install`. Le composant représente une installation distincte de l’application actuelle.<br />-   `preRequisite`. Le composant est requis par l’application actuelle.|  
|`codebase`|facultatif. Chemin d’accès complet au manifeste d’application.|  
|`size`|facultatif. Taille du manifeste de l’application, en octets.|  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 Obligatoire. Cet élément est un enfant de l’élément `dependentAssembly` . Le contenu de `assemblyIdentity` doit être le même que celui décrit dans le manifeste de l' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application. Le tableau suivant présente les attributs de l' `assemblyIdentity` élément.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Name`|Obligatoire. Identifie le nom de l’application.|  
|`Version`|Obligatoire. Spécifie le numéro de version de l’application, au format suivant : `major.minor.build.revision`|  
|`publicKeyToken`|Obligatoire. Spécifie une chaîne hexadécimale de 16 caractères qui représente les 8 derniers octets du hachage SHA-1 de la clé publique sous laquelle l’application ou l’assembly est signé. La clé publique utilisée pour la signature doit être supérieure ou égale à 2048 bits.|  
|`processorArchitecture`|Obligatoire. Spécifie le microprocesseur. Les valeurs valides sont `x86` pour les fenêtres 32 bits et `IA64` pour Windows 64 bits.|  
|`Language`|facultatif. Identifie les codes de langue en deux parties de l’assembly. Par exemple, en-US, qui correspond à l’anglais (États-Unis). Par défaut, il s’agit de `neutral`. Cet élément se trouve dans l' `asmv2` espace de noms.|  
|`type`|facultatif. Pour la compatibilité descendante avec la technologie d’installation côte à côte Windows. La seule valeur autorisée est `win32` .|  
  
## <a name="hash"></a>Hachage  
 L' `hash` élément est un enfant facultatif de l' `file` élément. L’élément `hash` ne comporte pas d’attributs.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] utilise un hachage algorithmique de tous les fichiers d’une application comme contrôle de sécurité pour s’assurer qu’aucun des fichiers n’a été modifié après le déploiement. Si l' `hash` élément n’est pas inclus, cette vérification ne sera pas effectuée. Par conséquent, l’omission de l' `hash` élément n’est pas recommandée.  
  
## <a name="dsigtransforms"></a>dsig:Transforms  
 L' `dsig:Transforms` élément est un enfant obligatoire de l' `hash` élément. L’élément `dsig:Transforms` ne comporte pas d’attributs.  
  
## <a name="dsigtransform"></a>dsig:Transform  
 L' `dsig:Transform` élément est un enfant obligatoire de l' `dsig:Transforms` élément. Le tableau suivant présente les attributs de l' `dsig:Transform` élément.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Algorithm`|Algorithme utilisé pour calculer le Digest pour ce fichier. Actuellement, la seule valeur utilisée par [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] est `urn:schemas-microsoft-com:HashTransforms.Identity` .|  
  
## <a name="dsigdigestmethod"></a>dsig:DigestMethod  
 L' `dsig:DigestMethod` élément est un enfant obligatoire de l' `hash` élément. Le tableau suivant présente les attributs de l' `dsig:DigestMethod` élément.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Algorithm`|Algorithme utilisé pour calculer le Digest pour ce fichier. Actuellement, la seule valeur utilisée par [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] est `http://www.w3.org/2000/09/xmldsig#sha1` .|  
  
## <a name="dsigdigestvalue"></a>dsig:DigestValue  
 L' `dsig:DigestValue` élément est un enfant obligatoire de l' `hash` élément. L’élément `dsig:DigestValue` ne comporte pas d’attributs. Sa valeur texte est le hachage calculé pour le fichier spécifié.  
  
## <a name="remarks"></a>Notes  
 Les manifestes de déploiement ont généralement un `assemblyIdentity` élément unique qui identifie le nom et la version du manifeste de l’application.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre un `dependency` élément dans un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifeste de déploiement.  
  
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
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant spécifie une dépendance sur un assembly déjà installé dans le GAC.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant spécifie une dépendance sur une version spécifique du common language runtime.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant spécifie une dépendance de système d’exploitation.  
  
```  
<dependency>  
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">  
      <osVersionInfo>  
         <os majorVersion="4" minorVersion="10" />  
      </osVersionInfo>  
   </dependentOS>  
</dependency>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [\<dependency> Appartient](../deployment/dependency-element-clickonce-application.md)
