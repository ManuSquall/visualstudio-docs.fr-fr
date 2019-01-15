---
title: '&lt;fichier&gt; , élément (Application ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
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
ms.openlocfilehash: c16c2cb00bf91d3fc0d991be71ba9b387d5a09cb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53828301"
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;fichier&gt; , élément (application ClickOnce)
Identifie tous les fichiers de l’autre téléchargé et utilisé par l’application.  

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
|`group`|Facultatif, si le `optional` attribut n’est pas spécifié ou la valeur `false`; obligatoire si `optional` est `true`. Le nom du groupe auquel appartient ce fichier. Le nom peut être toute valeur de chaîne Unicode choisi par le développeur et est utilisé pour télécharger des fichiers à la demande avec la <xref:System.Deployment.Application.ApplicationDeployment> classe.|  
|`optional`|Optionnel. Spécifie si ce fichier doit télécharger lorsque l’application est d’abord exécutée, ou si le fichier doit résider uniquement sur le serveur jusqu'à ce que l’application le demande à la demande. Si `false` ou non définie, le fichier est téléchargé lors de l’application est tout d’abord exécuter ou installée. Si `true`, un `group` doit être spécifié pour le manifeste d’application soit valide. `optional` ne peut pas être true si `writeableType` est spécifié avec la valeur `applicationData`.|  
|`writeableType`|Optionnel. Spécifie que ce fichier est un fichier de données. Actuellement, la seule valeur valide est `applicationData`.|  

## <a name="typelib"></a>bibliothèque de types  
 Le `typelib` élément est un enfant facultatif de l’élément de fichier. L’élément décrit la bibliothèque de types qui appartient au composant COM. L’élément a les attributs suivants.  

|Attribut|Description|  
|---------------|-----------------|  
|`tlbid`|Obligatoire. Le GUID affecté à la bibliothèque de types.|  
|`version`|Obligatoire. Le numéro de version de la bibliothèque de types.|  
|`helpdir`|Obligatoire. Le répertoire qui contient les fichiers d’aide pour le composant. Peut être de longueur nulle.|  
|`resourceid`|Optionnel. Représentation sous forme de chaîne hexadécimale de l’identificateur de paramètres régionaux (LCID). Il est d’un à quatre des chiffres hexadécimaux sans préfixe 0 x et sans zéros non significatifs. Le LCID peut avoir un identificateur de sous-langue neutre.|  
|`flags`|Optionnel. Représentation sous forme de chaîne des indicateurs de bibliothèque de type pour cette bibliothèque de types. Plus précisément, il doit être un des « RESTRICTED », « Contrôle », « HIDDEN » et « HASDISKIMAGE ».|  

## <a name="comclass"></a>comClass  
 Le `comClass` élément est un enfant facultatif de la `file` élément, mais il est obligatoire si le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application contient un composant COM qu’elle souhaite déployer à l’aide de COM sans inscription. L’élément a les attributs suivants.  

|Attribut|Description|  
|---------------|-----------------|  
|`clsid`|Obligatoire. L’ID de classe du composant COM exprimé sous la forme d’un GUID.|  
|`description`|Optionnel. Nom de la classe.|  
|`threadingModel`|Optionnel. Le modèle de thread utilisé par les classes COM intra-processus. Si cette propriété est null, aucun modèle de thread n’est utilisé. Le composant est créé sur le thread principal du client et les appels d’autres threads sont marshalés à ce thread. La liste suivante indique les valeurs valides :<br /><br /> `Apartment`, `Free`, `Both`et `Neutral`.|  
|`tlbid`|Optionnel. GUID de la bibliothèque de types pour ce composant COM.|  
|`progid`|Optionnel. Identificateur de programmation dépendants de la version associé au composant COM. Le format d’un `ProgID` est `<vendor>.<component>.<version>`.|  
|`miscStatus`|Optionnel. Les doublons dans l’assembly de manifeste les informations fournies par le `MiscStatus` clé de Registre. Si les valeurs pour le `miscStatusIcon`, `miscStatusContent`, `miscStatusDocprint`, ou `miscStatusThumbnail` attributs sont introuvables, la valeur par défaut correspondante répertoriée dans `miscStatus` est utilisé pour les attributs manquants. La valeur peut être une liste délimitée par des virgules des valeurs d’attribut dans le tableau suivant. Vous pouvez utiliser cet attribut si la classe COM est une classe OCX qui requiert `MiscStatus` les valeurs de clé de Registre.|  
|`miscStatusIcon`|Optionnel. Les doublons dans l’assembly de manifeste les informations fournies par DVASPECT_ICON. Il peut fournir une icône d’un objet. La valeur peut être une liste délimitée par des virgules des valeurs d’attribut dans le tableau suivant. Vous pouvez utiliser cet attribut si la classe COM est une classe OCX qui requiert `Miscstatus` les valeurs de clé de Registre.|  
|`miscStatusContent`|Optionnel. Les doublons dans l’assembly de manifeste les informations fournies par DVASPECT_CONTENT. Il peut fournir un document composé affichable pour un écran ou une imprimante. La valeur peut être une liste délimitée par des virgules des valeurs d’attribut dans le tableau suivant. Vous pouvez utiliser cet attribut si la classe COM est une classe OCX qui requiert `MiscStatus` les valeurs de clé de Registre.|  
|`miscStatusDocPrint`|Optionnel. Les doublons dans l’assembly de manifeste les informations fournies par DVASPECT_DOCPRINT. Il peut fournir une représentation d’objet affichable sur l’écran comme si vous a adressé à une imprimante. La valeur peut être une liste délimitée par des virgules des valeurs d’attribut dans le tableau suivant. Vous pouvez utiliser cet attribut si la classe COM est une classe OCX qui requiert `MiscStatus` les valeurs de clé de Registre.|  
|`miscStatusThumbnail`|Optionnel. Les doublons dans un assembly de manifeste les informations fournies par DVASPECT_THUMBNAIL. Il peut fournir une miniature d’un objet affichable dans un outil de navigation. La valeur peut être une liste délimitée par des virgules des valeurs d’attribut dans le tableau suivant. Vous pouvez utiliser cet attribut si la classe COM est une classe OCX qui requiert `MiscStatus` les valeurs de clé de Registre.|  

## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub  
 Le `comInterfaceExternalProxyStub` élément est un enfant facultatif de la `file` élément, mais peut être nécessaire si le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application contient un composant COM qu’elle souhaite déployer à l’aide de COM sans inscription. L’élément contient les attributs suivants.  

|Attribut|Description|  
|---------------|-----------------|  
|`iid`|Obligatoire. L’ID d’interface (IID) pris en charge par ce proxy. L’IID doit être entre accolades.|  
|`baseInterface`|Optionnel. IID de l’interface à partir de laquelle l’interface référencée par `iid` est dérivée.|  
|`numMethods`|Optionnel. Le nombre de méthodes implémentées par l’interface.|  
|`name`|Optionnel. Le nom de l’interface tel qu’il apparaîtra dans le code.|  
|`tlbid`|Optionnel. La bibliothèque de types qui contient la description de l’interface spécifiée par le `iid` attribut.|  
|`proxyStubClass32`|Optionnel. Mappe un IID à un CLSID dans la DLL de proxy de 32 bits.|  

## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub  
 Le `comInterfaceProxyStub` élément est un enfant facultatif de la `file` élément, mais peut être nécessaire si le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application contient un composant COM qu’elle souhaite déployer à l’aide de COM sans inscription. L’élément contient les attributs suivants.  

|Attribut|Description|  
|---------------|-----------------|  
|`iid`|Obligatoire. L’ID d’interface (IID) pris en charge par ce proxy. L’IID doit être entre accolades.|  
|`baseInterface`|Optionnel. IID de l’interface à partir de laquelle l’interface référencée par `iid` est dérivée.|  
|`numMethods`|Optionnel. Le nombre de méthodes implémentées par l’interface.|  
|`Name`|Optionnel. Le nom de l’interface tel qu’il apparaîtra dans le code.|  
|`Tlbid`|Optionnel. La bibliothèque de types qui contient la description de l’interface spécifiée par le `iid` attribut.|  
|`proxyStubClass32`|Optionnel. Mappe un IID à un CLSID dans la DLL de proxy de 32 bits.|  
|`threadingModel`|Optionnel. Optionnel. Le modèle de thread utilisé par les classes COM intra-processus. Si cette propriété est null, aucun modèle de thread n’est utilisé. Le composant est créé sur le thread principal du client et les appels d’autres threads sont marshalés à ce thread. La liste suivante indique les valeurs valides :<br /><br /> `Apartment`, `Free`, `Both`et `Neutral`.|  

## <a name="windowclass"></a>windowClass  
 Le `windowClass` élément est un enfant facultatif de la `file` élément, mais peut être nécessaire si le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application contient un composant COM qu’elle souhaite déployer à l’aide de COM sans inscription. L’élément fait référence à une classe de fenêtre définie par le composant COM qui doit avoir une version appliquée. L’élément contient les attributs suivants.  

|Attribut|Description|  
|---------------|-----------------|  
|`versioned`|Optionnel. Contrôle si la fenêtre interne nom de la classe utilisé dans l’inscription contient la version de l’assembly qui contient la classe de fenêtre. La valeur de cet attribut peut être `yes` ou `no`. La valeur par défaut est `yes`. La valeur `no` doit être utilisé uniquement si la même classe de fenêtre est définie par un composant côte à côte et un composant non côte-à-côte équivalent et que vous souhaitez les traiter comme la même classe de fenêtre. Notez que les règles habituelles concernant l’inscription de classe de fenêtre s’appliquent : seul le premier composant qui enregistre la classe de fenêtre sera capable de l’enregistrer, car il ne dispose pas d’une version appliquée.|  

## <a name="hash"></a>hash  
 Le `hash` élément est un enfant facultatif de la `file` élément. L’élément `hash` ne comporte pas d’attributs.  

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utilise un hachage algorithmique de tous les fichiers dans une application en tant qu’une vérification de sécurité, pour vous assurer qu’aucun des fichiers ont été modifiés après le déploiement. Si le `hash` élément n’est pas inclus, cette vérification ne sera pas effectuée. Par conséquent, en omettant le `hash` élément n’est pas recommandé.  

 Si un manifeste contient un fichier qui n’est pas haché, ce manifeste ne peut pas être numériquement signé, car les utilisateurs ne peuvent pas vérifier le contenu d’un fichier non hachée.  

## <a name="dsigtransforms"></a>dsig : TRANSFORMS  
 Le `dsig:Transforms` élément est un enfant requis de le `hash` élément. L’élément `dsig:Transforms` ne comporte pas d’attributs.  

## <a name="dsigtransform"></a>dsig : Transform  
 Le `dsig:Transform` élément est un enfant requis de le `dsig:Transforms` élément. L’élément `dsig:Transform` a les attributs suivants.  


| Attribut | Description |
|-------------| - |
| `Algorithm` | L’algorithme utilisé pour calculer le condensat pour ce fichier. La seule valeur utilisée par [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est `urn:schemas-microsoft-com:HashTransforms.Identity`. |

## <a name="dsigdigestmethod"></a>dsig:DigestMethod  
 Le `dsig:DigestMethod` élément est un enfant requis de le `hash` élément. L’élément `dsig:DigestMethod` a les attributs suivants.  


| Attribut | Description |
|-------------| - |
| `Algorithm` | L’algorithme utilisé pour calculer le condensat pour ce fichier. La seule valeur utilisée par [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est `http://www.w3.org/2000/09/xmldsig#sha1`. |

## <a name="dsigdigestvalue"></a>dsig : DigestValue  
 Le `dsig:DigestValue` élément est un enfant requis de le `hash` élément. L’élément `dsig:DigestValue` ne comporte pas d’attributs. Sa valeur de texte est le hachage calculé pour le fichier spécifié.  

## <a name="remarks"></a>Notes  
 Cet élément identifie tous les fichiers d’autres qui composent l’application et, en particulier, les valeurs de hachage de fichier de vérification. Cet élément peut également inclure des données d’isolation de composant COM (Object Model) associées au fichier. Si un fichier est modifié, le fichier manifeste d’application également doit être mis à jour pour refléter la modification.  

## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre `file` manifeste des éléments dans une application pour une application déployée à l’aide de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  

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