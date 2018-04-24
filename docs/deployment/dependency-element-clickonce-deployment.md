---
title: '&lt;dépendance&gt; élément (déploiement ClickOnce) | Documents Microsoft'
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
- <dependency> element [ClickOnce deployment manifest]
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 72e217413a428c8c22712ac3a90836b1ea4fbc35
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;dépendance&gt; élément (déploiement ClickOnce)
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
 Le `dependency` élément est requis. Il possède pas d’attributs. Un manifeste de déploiement peut avoir plusieurs `dependency` éléments.  
  
 Le `dependency` élément décrit habituellement des dépendances de l’application principale avec des assemblys contenus dans un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application. Si votre application Main.exe utilise un assembly appelé DotNetAssembly.dll, doit être répertorié dans une section de dépendance. Dépendance, toutefois, peut également s’exprimer autres types de dépendances, tels que des dépendances sur une version spécifique du common language runtime, sur un assembly dans le global assembly cache (GAC), ou sur un objet COM. S’agissant d’une technologie de déploiement no-touch, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ne peut pas initialiser le téléchargement et installation de ces types de dépendances, mais il empêche l’application de s’exécuter si une ou plusieurs des dépendances spécifiées n’existent pas.  
  
## <a name="dependentassembly"></a>dependentAssembly  
 Obligatoire. Cet élément contient le `assemblyIdentity` élément. Le tableau suivant montre les attributs du `dependentAssembly` prend en charge.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`preRequisite`|Facultatif. Spécifie que cet assembly doit déjà exister dans le GAC. Les valeurs valides sont `true` et `false`. Si `true`et l’assembly spécifié n’existe pas dans le GAC, l’application ne s’exécute.|  
|`visible`|Facultatif. Identifie l’identité de l’application de niveau supérieur, y compris ses dépendances. Utilisé en interne par [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pour gérer le stockage d’application et d’activation.|  
|`dependencyType`|Obligatoire. La relation entre cette dépendance et l’application. Les valeurs valides sont les suivantes :<br /><br /> -   `install`. Composant représente une installation distincte de l’application actuelle.<br />-   `preRequisite`. Composant est requis par l’application actuelle.|  
|`codebase`|Facultatif. Le chemin d’accès complet au manifeste d’application.|  
|`size`|Facultatif. La taille du manifeste d’application, en octets.|  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 Obligatoire. Cet élément est un enfant de l’élément `dependentAssembly`. Le contenu de `assemblyIdentity` doit être identique à celui décrit dans la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeste d’application. Le tableau suivant présente les attributs de la `assemblyIdentity` élément.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Name`|Obligatoire. Identifie le nom de l’application.|  
|`Version`|Obligatoire. Spécifie le numéro de version de l’application, dans le format suivant : `major.minor.build.revision`|  
|`publicKeyToken`|Obligatoire. Spécifie une chaîne hexadécimale de 16 caractères qui représente les 8 derniers octets du hachage SHA-1 de la clé publique sous laquelle l’application ou l’assembly est signé. La clé publique utilisée pour se connecter doit être de 2 048 bits ou supérieur.|  
|`processorArchitecture`|Obligatoire. Spécifie le microprocesseur. Les valeurs valides sont `x86` pour Windows 32 bits et `IA64` pour Windows 64 bits.|  
|`Language`|Facultatif. Identifie les codes de langue de deux parties de l’assembly. Par exemple, EN-US, qui est l’abréviation pour l’anglais (États-Unis). La valeur par défaut est `neutral`. Cet élément est dans le `asmv2` espace de noms.|  
|`type`|Facultatif. Pour descendante compatibilité avec côte à côte de Windows Installer technologie. La seule valeur autorisée est `win32`.|  
  
## <a name="hash"></a>hash  
 Le `hash` élément est un enfant facultatif de la `file` élément. Le `hash` élément ne possède pas d’attributs.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utilise un hachage algorithmique de tous les fichiers dans une application en tant qu’une vérification de sécurité pour vous assurer qu’aucun des fichiers ont été modifiées après le déploiement. Si le `hash` élément n’est pas inclus, cette vérification ne sera pas effectuée. Par conséquent, l’omission de la `hash` élément n’est pas recommandé.  
  
## <a name="dsigtransforms"></a>dsig : TRANSFORMS  
 Le `dsig:Transforms` élément est un enfant requis de le `hash` élément. Le `dsig:Transforms` élément ne possède pas d’attributs.  
  
## <a name="dsigtransform"></a>dsig : Transform  
 Le `dsig:Transform` élément est un enfant requis de le `dsig:Transforms` élément. Le tableau suivant présente les attributs de la `dsig:Transform` élément.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Algorithm`|L’algorithme utilisé pour calculer le digest pour ce fichier. La seule valeur utilisée par [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
## <a name="dsigdigestmethod"></a>dsig:DigestMethod  
 Le `dsig:DigestMethod` élément est un enfant requis de le `hash` élément. Le tableau suivant présente les attributs de la `dsig:DigestMethod` élément.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Algorithm`|L’algorithme utilisé pour calculer le digest pour ce fichier. La seule valeur utilisée par [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
## <a name="dsigdigestvalue"></a>dsig : DigestValue  
 Le `dsig:DigestValue` élément est un enfant requis de le `hash` élément. Le `dsig:DigestValue` élément ne possède pas d’attributs. Sa valeur texte est le hachage calculé pour le fichier spécifié.  
  
## <a name="remarks"></a>Notes  
 Manifestes de déploiement possèdent en général un seul `assemblyIdentity` qui identifie le nom et la version du manifeste d’application.  
  
## <a name="example"></a>Exemple  
 Le code suivant exemple illustre un `dependency` élément dans un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeste de déploiement.  
  
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
 [\<dépendance > élément](../deployment/dependency-element-clickonce-application.md)