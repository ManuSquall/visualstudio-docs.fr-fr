---
title: '&lt;dépendance&gt; , élément (déploiement ClickOnce) | Microsoft Docs'
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950012"
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;dépendance&gt; , élément (déploiement ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifie la version de l’application à installer et l’emplacement du manifeste d’application.  
  
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
 Le `dependency` élément est requis. Il a pas d’attributs. Un manifeste de déploiement peut avoir plusieurs `dependency` éléments.  
  
 Le `dependency` élément décrit généralement les dépendances de l’application principale sur les assemblys contenus dans un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application. Si votre application Main.exe utilise un assembly appelé DotNetAssembly.dll, cet assembly doit être répertorié dans une section de dépendance. Dépendance, toutefois, permettre également exprimer autres types de dépendances, telles que les dépendances sur une version spécifique du common language runtime, sur un assembly dans le global assembly cache (GAC) ou sur un objet COM. S’agissant d’une technologie de déploiement sans peine, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ne peut pas initialiser le téléchargement et installation de ces types de dépendances, mais il n’empêche l’application de s’exécuter si une ou plusieurs des dépendances spécifiées n’existent pas.  
  
## <a name="dependentassembly"></a>dependentAssembly  
 Obligatoire. Cet élément contient le `assemblyIdentity` élément. Le tableau suivant présente les attributs du `dependentAssembly` prend en charge.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`preRequisite`|Facultatif. Spécifie que cet assembly doit déjà exister dans le GAC. Les valeurs valides sont `true` et `false`. Si `true`et l’assembly spécifié n’existe pas dans le GAC, l’application ne parvient pas à exécuter.|  
|`visible`|Facultatif. Identifie l’identité de l’application de niveau supérieur, y compris ses dépendances. Utilisé en interne par [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] pour gérer le stockage des applications et l’activation.|  
|`dependencyType`|Obligatoire. La relation entre cette dépendance et l’application. Les valeurs valides sont les suivantes :<br /><br /> -   `install`. Composant représente une installation distincte de l’application actuelle.<br />-   `preRequisite`. Composant est requis par l’application actuelle.|  
|`codebase`|Optionnel. Le chemin d’accès complet au manifeste d’application.|  
|`size`|Optionnel. La taille du manifeste d’application, en octets.|  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 Obligatoire. Cet élément est un enfant de l’élément `dependentAssembly` . Le contenu de `assemblyIdentity` doit être identique à celui décrit dans la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifeste d’application. Le tableau suivant présente les attributs de la `assemblyIdentity` élément.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Name`|Obligatoire. Identifie le nom de l’application.|  
|`Version`|Obligatoire. Spécifie le numéro de version de l’application, dans le format suivant : `major.minor.build.revision`|  
|`publicKeyToken`|Obligatoire. Spécifie une chaîne hexadécimale de 16 caractères qui représente les 8 derniers octets du hachage SHA-1 de la clé publique sous laquelle l’application ou l’assembly est signé. La clé publique utilisée pour se connecter doit être de 2 048 bits ou supérieur.|  
|`processorArchitecture`|Obligatoire. Spécifie le microprocesseur. Les valeurs valides sont `x86` pour 32 bits Windows et `IA64` pour Windows de 64 bits.|  
|`Language`|Optionnel. Identifie les codes de langue de deux parties de l’assembly. Par exemple, EN-US, qui signifie pour l’anglais (US). La valeur par défaut est `neutral`. Cet élément est dans le `asmv2` espace de noms.|  
|`type`|Facultatif. Pour assurer la compatibilité avec Windows côte à côte vers l’arrière, installez technologie. La seule valeur autorisée est `win32`.|  
  
## <a name="hash"></a>hash  
 Le `hash` élément est un enfant facultatif de la `file` élément. L’élément `hash` ne comporte pas d’attributs.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] utilise un hachage algorithmique de tous les fichiers dans une application en tant qu’une vérification de sécurité pour vous assurer qu’aucun des fichiers ont été modifiés après le déploiement. Si le `hash` élément n’est pas inclus, cette vérification ne sera pas effectuée. Par conséquent, en omettant le `hash` élément n’est pas recommandé.  
  
## <a name="dsigtransforms"></a>dsig:Transforms  
 Le `dsig:Transforms` élément est un enfant requis de le `hash` élément. L’élément `dsig:Transforms` ne comporte pas d’attributs.  
  
## <a name="dsigtransform"></a>dsig:Transform  
 Le `dsig:Transform` élément est un enfant requis de le `dsig:Transforms` élément. Le tableau suivant présente les attributs de la `dsig:Transform` élément.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Algorithm`|L’algorithme utilisé pour calculer le condensat pour ce fichier. La seule valeur utilisée par [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] est `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
## <a name="dsigdigestmethod"></a>dsig:DigestMethod  
 Le `dsig:DigestMethod` élément est un enfant requis de le `hash` élément. Le tableau suivant présente les attributs de la `dsig:DigestMethod` élément.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Algorithm`|L’algorithme utilisé pour calculer le condensat pour ce fichier. La seule valeur utilisée par [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] est `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
## <a name="dsigdigestvalue"></a>dsig:DigestValue  
 Le `dsig:DigestValue` élément est un enfant requis de le `hash` élément. L’élément `dsig:DigestValue` ne comporte pas d’attributs. Sa valeur de texte est le hachage calculé pour le fichier spécifié.  
  
## <a name="remarks"></a>Notes  
 Manifestes de déploiement possèdent généralement un seul `assemblyIdentity` élément qui identifie le nom et la version du manifeste d’application.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre l’exemple un `dependency` élément dans un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifeste de déploiement.  
  
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
 [\<dependency>, élément](../deployment/dependency-element-clickonce-application.md)
