---
title: '&lt;fichier&gt; élément (déploiement ClickOnce) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#file
- http://www.w3.org/2000/09/xmldsig#DigestValue
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <file> element [ClickOnce application manifest]
- manifests [ClickOnce], file element
ms.assetid: 56e3490c-eed5-4841-b1bf-eefe778b6ac9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f1e744071219426c751576f8ca781ad27dfedb61
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815847"
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;fichier&gt; élément (déploiement ClickOnce)
Identifie tous les autres fichiers, téléchargé et utilisé par l’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<file  
    name  
    size  
    group  
    optional  
    writeableType  
>  
    <typelib  
        tlbid  
        version  
        helpdir  
        resourceid  
        flags  
    />  
    <comClass  
        clsid  
        description  
        threadingModel  
        tlbid  
        progid  
        miscStatus  
        miscStatusIcon  
        miscStatusContent  
        miscStatusDocPrint  
        miscStatusThumbnail  
    />  
    <comInterfaceExternalProxyStub  
        iid  
        baseInterface  
        numMethods  
        name  
        tlbid  
        proxyStubClass32  
    />  
    <comInterfaceProxyStub  
        iid  
        baseInterface  
        numMethods  
        name  
        tlbid  
        proxyStubClass32  
    />  
    <windowClass  
        versioned  
    />  
</file>  
```  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 L’élément `file` est facultatif. L’élément a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`name`|Obligatoire. Identifie le nom du fichier.|  
|`size`|Obligatoire. Spécifie la taille, en octets, du fichier.|  
|`group`|Facultatif si le `optional` attribut n’est pas spécifié ou la valeur `false`; obligatoire si `optional` est `true`. Le nom du groupe auquel appartient ce fichier. Le nom peut être toute valeur de chaîne Unicode choisi par le développeur et est utilisé pour télécharger les fichiers à la demande avec la <xref:System.Deployment.Application.ApplicationDeployment> classe.|  
|`optional`|Facultatif. Spécifie si ce fichier doit télécharger lorsque l’application est d’abord exécuter, ou si le fichier doit résider uniquement sur le serveur jusqu'à ce que l’application le demande à la demande. Si `false` ou non définie, le fichier est téléchargé lors de l’application est tout d’abord exécuter ou installée. Si `true`, un `group` doit être spécifié pour le manifeste d’application valide. `optional` ne peut pas avoir la valeur true si `writeableType` est spécifié avec la valeur `applicationData`.|  
|`writeableType`|Facultatif. Spécifie que ce fichier est un fichier de données. Actuellement la seule valeur valide est `applicationData`.|  
  
## <a name="typelib"></a>bibliothèque de types  
 Le `typelib` élément est un enfant facultatif de l’élément de fichier. L’élément décrit la bibliothèque de types auquel appartient le composant COM. L’élément a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`tlbid`|Obligatoire. Le GUID affecté à la bibliothèque de types.|  
|`version`|Obligatoire. Le numéro de version de la bibliothèque de types.|  
|`helpdir`|Obligatoire. Le répertoire qui contient les fichiers d’aide pour le composant. Peut être de longueur zéro.|  
|`resourceid`|Facultatif. La représentation sous forme de chaîne hexadécimale de l’identificateur de paramètres régionaux (LCID). Il est d’un à quatre hexadécimaux sans préfixe 0 x et sans zéros non significatifs. Le LCID peut avoir un identificateur de sous-langue neutre.|  
|`flags`|Facultatif. La représentation sous forme de chaîne des indicateurs de bibliothèque de type pour cette bibliothèque de types. Plus précisément, elle doit être un des « RESTRICTED », « Contrôle », « HIDDEN » et « HASDISKIMAGE ».|  
  
## <a name="comclass"></a>comClass  
 Le `comClass` élément est un enfant facultatif de la `file` élément, mais il est obligatoire si le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application contient un composant COM qu’il a l’intention de déployer à l’aide de COM sans inscription. L’élément a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`clsid`|Obligatoire. L’ID de classe du composant COM exprimée sous la forme d’un GUID.|  
|`description`|Facultatif. Nom de la classe.|  
|`threadingModel`|Facultatif. Le modèle de thread utilisé par les classes COM intra-processus. Si cette propriété est null, aucun modèle de thread n’est utilisé. Le composant est créé sur le thread principal du client et les appels d’autres threads sont marshalés à ce thread. La liste suivante indique les valeurs valides :<br /><br /> `Apartment`, `Free`, `Both` et `Neutral`.|  
|`tlbid`|Facultatif. GUID de la bibliothèque de types pour ce composant COM.|  
|`progid`|Facultatif. Identificateur de programme dépendant de la version associée au composant COM. Le format d’un `ProgID` est `<vendor>.<component>.<version>`.|  
|`miscStatus`|Facultatif. Les doublons dans l’assembly de manifeste les informations fournies par le `MiscStatus` clé de Registre. Si les valeurs pour le `miscStatusIcon`, `miscStatusContent`, `miscStatusDocprint`, ou `miscStatusThumbnail` attribut n’est pas trouvé, la valeur par défaut correspondante répertoriée dans `miscStatus` est utilisé pour les attributs manquants. La valeur peut être une liste délimitée par des virgules des valeurs d’attribut dans le tableau suivant. Vous pouvez utiliser cet attribut si la classe COM est une classe OCX qui requiert `MiscStatus` les valeurs de clé de Registre.|  
|`miscStatusIcon`|Facultatif. Les doublons dans l’assembly de manifeste les informations fournies par DVASPECT_ICON. Il peut fournir une icône d’un objet. La valeur peut être une liste délimitée par des virgules des valeurs d’attribut dans le tableau suivant. Vous pouvez utiliser cet attribut si la classe COM est une classe OCX qui requiert `Miscstatus` les valeurs de clé de Registre.|  
|`miscStatusContent`|Facultatif. Les doublons dans l’assembly de manifeste les informations fournies par DVASPECT_CONTENT. Il peut fournir un document composé peut être affichée pour un écran ou une imprimante. La valeur peut être une liste délimitée par des virgules des valeurs d’attribut dans le tableau suivant. Vous pouvez utiliser cet attribut si la classe COM est une classe OCX qui requiert `MiscStatus` les valeurs de clé de Registre.|  
|`miscStatusDocPrint`|Facultatif. Les doublons dans l’assembly de manifeste les informations fournies par DVASPECT_DOCPRINT. Il peut fournir une représentation d’objet peut être affichée sur l’écran comme si l’impression sur une imprimante. La valeur peut être une liste délimitée par des virgules des valeurs d’attribut dans le tableau suivant. Vous pouvez utiliser cet attribut si la classe COM est une classe OCX qui requiert `MiscStatus` les valeurs de clé de Registre.|  
|`miscStatusThumbnail`|Facultatif. Les doublons dans un assembly de manifeste les informations fournies par DVASPECT_THUMBNAIL. Il peut fournir une miniature d’un objet peut être affichée dans un outil de navigation. La valeur peut être une liste délimitée par des virgules des valeurs d’attribut dans le tableau suivant. Vous pouvez utiliser cet attribut si la classe COM est une classe OCX qui requiert `MiscStatus` les valeurs de clé de Registre.|  
  
## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub  
 Le `comInterfaceExternalProxyStub` élément est un enfant facultatif de la `file` élément, mais peut être nécessaire si le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application contient un composant COM qu’il a l’intention de déployer à l’aide de COM sans inscription. L’élément contient les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`iid`|Obligatoire. L’interface ID (IID) est pris en charge par ce serveur proxy. L’IID doit être entre accolades.|  
|`baseInterface`|Facultatif. IID de l’interface à partir de laquelle l’interface référencée par `iid` est dérivée.|  
|`numMethods`|Facultatif. Le nombre de méthodes implémentées par l’interface.|  
|`name`|Facultatif. Le nom de l’interface tel qu’il apparaîtra dans le code.|  
|`tlbid`|Facultatif. La bibliothèque de types qui contient la description de l’interface spécifiée par le `iid` attribut.|  
|`proxyStubClass32`|Facultatif. Mappe un IID à un CLSID dans la DLL de proxy 32 bits.|  
  
## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub  
 Le `comInterfaceProxyStub` élément est un enfant facultatif de la `file` élément, mais peut être nécessaire si le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application contient un composant COM qu’il a l’intention de déployer à l’aide de COM sans inscription. L’élément contient les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`iid`|Obligatoire. L’interface ID (IID) est pris en charge par ce serveur proxy. L’IID doit être entre accolades.|  
|`baseInterface`|Facultatif. IID de l’interface à partir de laquelle l’interface référencée par `iid` est dérivée.|  
|`numMethods`|Facultatif. Le nombre de méthodes implémentées par l’interface.|  
|`Name`|Facultatif. Le nom de l’interface tel qu’il apparaîtra dans le code.|  
|`Tlbid`|Facultatif. La bibliothèque de types qui contient la description de l’interface spécifiée par le `iid` attribut.|  
|`proxyStubClass32`|Facultatif. Mappe un IID à un CLSID dans la DLL de proxy 32 bits.|  
|`threadingModel`|Facultatif. Facultatif. Le modèle de thread utilisé par les classes COM intra-processus. Si cette propriété est null, aucun modèle de thread n’est utilisé. Le composant est créé sur le thread principal du client et les appels d’autres threads sont marshalés à ce thread. La liste suivante indique les valeurs valides :<br /><br /> `Apartment`, `Free`, `Both` et `Neutral`.|  
  
## <a name="windowclass"></a>windowClass  
 Le `windowClass` élément est un enfant facultatif de la `file` élément, mais peut être nécessaire si le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application contient un composant COM qu’il a l’intention de déployer à l’aide de COM sans inscription. L’élément fait référence à une classe de fenêtre définie par le composant COM qui doit avoir une version appliquée. L’élément contient les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`versioned`|Facultatif. Contrôle si la fenêtre interne nom de la classe utilisé dans l’inscription contient la version de l’assembly qui contient la classe de fenêtre. La valeur de cet attribut peut être `yes` ou `no`. La valeur par défaut est `yes`. La valeur `no` doit être utilisé uniquement si la même classe de fenêtre est définie par un composant côte à côte et d’un équivalent du composant non côte-à-côte et vous souhaitez les traiter comme la même classe de fenêtre. Notez que les règles habituelles concernant l’inscription de classe de fenêtre s’appliquent : seul le premier composant qui enregistre la classe de fenêtre sera capable de l’enregistrer, car il ne dispose pas d’une version appliquée.|  
  
## <a name="hash"></a>hash  
 Le `hash` élément est un enfant facultatif de la `file` élément. Le `hash` élément ne possède pas d’attributs.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utilise un hachage algorithmique de tous les fichiers dans une application en tant qu’une vérification de sécurité pour vous assurer qu’aucun des fichiers ont été modifiées après le déploiement. Si le `hash` élément n’est pas inclus, cette vérification ne sera pas effectuée. Par conséquent, l’omission de la `hash` élément n’est pas recommandé.  
  
 Si un manifeste contienne un fichier qui n’est pas haché, ce manifeste ne peut pas être numériquement signé, car les utilisateurs ne peuvent pas vérifier le contenu d’un fichier non hachée.  
  
## <a name="dsigtransforms"></a>dsig : TRANSFORMS  
 Le `dsig:Transforms` élément est un enfant requis de le `hash` élément. Le `dsig:Transforms` élément ne possède pas d’attributs.  
  
## <a name="dsigtransform"></a>dsig : Transform  
 Le `dsig:Transform` élément est un enfant requis de le `dsig:Transforms` élément. Le `dsig:Transform` élément a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Algorithm`|L’algorithme utilisé pour calculer le digest pour ce fichier. La seule valeur utilisée par [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
## <a name="dsigdigestmethod"></a>dsig:DigestMethod  
 Le `dsig:DigestMethod` élément est un enfant requis de le `hash` élément. Le `dsig:DigestMethod` élément a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Algorithm`|L’algorithme utilisé pour calculer le digest pour ce fichier. La seule valeur utilisée par [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
## <a name="dsigdigestvalue"></a>dsig : DigestValue  
 Le `dsig:DigestValue` élément est un enfant requis de le `hash` élément. Le `dsig:DigestValue` élément ne possède pas d’attributs. Sa valeur texte est le hachage calculé pour le fichier spécifié.  
  
## <a name="remarks"></a>Notes  
 Cet élément identifie tous les fichiers autres que l’application et, en particulier, les valeurs de hachage de vérification des fichiers. Cet élément peut également inclure des données d’isolation de modèle COM (Component Object) associées au fichier. Si un fichier est modifié, le fichier manifeste d’application également doit être mis à jour pour refléter les modifications.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre `file` le manifeste d’éléments dans une application pour une application déployée à l’aide de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
```xml  
<file name="Icon.ico" size="9216">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>lVoj+Rh6RQ/HPNLOdayQah5McrI=</dsig:DigestValue>  
  </hash>  
</file>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)