---
title: '&lt;file &gt; , élément (application ClickOnce) | Microsoft Docs'
description: L’élément file identifie tous les fichiers non assembly téléchargés et utilisés par l’application. L’élément file est facultatif.
ms.custom: SEO-VS-2020
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a4d09d4a0e141359b066f2af31c158f36c96522
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382739"
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;file &gt; , élément (application ClickOnce)
Identifie tous les fichiers non assembly téléchargés et utilisés par l’application.

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
|`group`|Facultatif, si l' `optional` attribut n’est pas spécifié ou a la valeur `false` ; obligatoire si `optional` est `true` . Nom du groupe auquel ce fichier appartient. Le nom peut être n’importe quelle valeur de chaîne Unicode choisie par le développeur et est utilisé pour télécharger des fichiers à la demande avec la <xref:System.Deployment.Application.ApplicationDeployment> classe.|
|`optional`|facultatif. Spécifie si ce fichier doit être téléchargé lorsque l’application est exécutée pour la première fois, ou si le fichier doit résider uniquement sur le serveur jusqu’à ce que l’application le demande à la demande. Si `false` ou n’est pas défini, le fichier est téléchargé lors de la première exécution ou de l’installation de l’application. Si `true` `group` la valeur est, un doit être spécifié pour que le manifeste d’application soit valide. `optional` ne peut pas avoir la valeur true si `writeableType` est spécifié avec la valeur `applicationData` .|
|`writeableType`|facultatif. Spécifie que ce fichier est un fichier de données. Actuellement, la seule valeur valide est `applicationData`.|

## <a name="typelib"></a>typelib
 L' `typelib` élément est un enfant facultatif de l’élément file. L’élément décrit la bibliothèque de types qui appartient au composant COM. L’élément a les attributs suivants.

|Attribut|Description|
|---------------|-----------------|
|`tlbid`|Obligatoire. GUID affecté à la bibliothèque de types.|
|`version`|Obligatoire. Numéro de version de la bibliothèque de types.|
|`helpdir`|Obligatoire. Répertoire qui contient les fichiers d’aide du composant. Peut être de longueur nulle.|
|`resourceid`|facultatif. Représentation sous forme de chaîne hexadécimale de l’identificateur de paramètres régionaux (LCID). Il s’agit d’un à quatre chiffres hexadécimaux sans préfixe 0x et sans zéros non significatifs. Le LCID peut avoir un identificateur de sous-langue neutre.|
|`flags`|facultatif. Représentation sous forme de chaîne des indicateurs de la bibliothèque de types pour cette bibliothèque de types. En particulier, il doit s’agir de « RESTRICTED », « CONTROL », « HIDDEN » et « HASDISKIMAGE ».|

## <a name="comclass"></a>comClass
 L' `comClass` élément est un enfant facultatif de l' `file` élément, mais est requis si l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application contient un composant COM qu’il envisage de déployer à l’aide de com sans inscription. L’élément a les attributs suivants.

|Attribut|Description|
|---------------|-----------------|
|`clsid`|Obligatoire. ID de classe du composant COM exprimé sous la forme d’un GUID.|
|`description`|facultatif. Nom de la classe.|
|`threadingModel`|facultatif. Modèle de thread utilisé par les classes COM in-process. Si cette propriété a la valeur null, aucun modèle de thread n’est utilisé. Le composant est créé sur le thread principal du client et les appels d’autres threads sont marshalés vers ce thread. La liste suivante affiche les valeurs valides :<br /><br /> `Apartment`, `Free`, `Both` et `Neutral`.|
|`tlbid`|facultatif. GUID de la bibliothèque de types pour ce composant COM.|
|`progid`|facultatif. Identificateur programmatique dépendant de la version associé au composant COM. Le format d’un `ProgID` est `<vendor>.<component>.<version>` .|
|`miscStatus`|facultatif. Les doublons dans le manifeste de l’assembly sont les informations fournies par la `MiscStatus` clé de registre. Si les valeurs des `miscStatusIcon` `miscStatusContent` attributs,, `miscStatusDocprint` ou `miscStatusThumbnail` sont introuvables, la valeur par défaut correspondante répertoriée dans `miscStatus` est utilisée pour les attributs manquants. La valeur peut être une liste délimitée par des virgules des valeurs d’attribut du tableau suivant. Vous pouvez utiliser cet attribut si la classe COM est une classe OCX qui requiert des `MiscStatus` valeurs de clé de registre.|
|`miscStatusIcon`|facultatif. Les doublons dans le manifeste de l’assembly sont les informations fournies par DVASPECT_ICON. Il peut fournir une icône d’un objet. La valeur peut être une liste délimitée par des virgules des valeurs d’attribut du tableau suivant. Vous pouvez utiliser cet attribut si la classe COM est une classe OCX qui requiert des `Miscstatus` valeurs de clé de registre.|
|`miscStatusContent`|facultatif. Les doublons dans le manifeste de l’assembly sont les informations fournies par DVASPECT_CONTENT. Il peut fournir un document composé affichable pour un écran ou une imprimante. La valeur peut être une liste délimitée par des virgules des valeurs d’attribut du tableau suivant. Vous pouvez utiliser cet attribut si la classe COM est une classe OCX qui requiert des `MiscStatus` valeurs de clé de registre.|
|`miscStatusDocPrint`|facultatif. Les doublons dans le manifeste de l’assembly sont les informations fournies par DVASPECT_DOCPRINT. Il peut fournir une représentation d’objet affichable sur l’écran comme s’il était imprimé sur une imprimante. La valeur peut être une liste délimitée par des virgules des valeurs d’attribut du tableau suivant. Vous pouvez utiliser cet attribut si la classe COM est une classe OCX qui requiert des `MiscStatus` valeurs de clé de registre.|
|`miscStatusThumbnail`|facultatif. Doublons dans un manifeste d’assembly les informations fournies par DVASPECT_THUMBNAIL. Il peut fournir une miniature d’un objet affichable dans un outil de navigation. La valeur peut être une liste délimitée par des virgules des valeurs d’attribut du tableau suivant. Vous pouvez utiliser cet attribut si la classe COM est une classe OCX qui requiert des `MiscStatus` valeurs de clé de registre.|

## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub
 L' `comInterfaceExternalProxyStub` élément est un enfant facultatif de l' `file` élément, mais il peut être nécessaire si l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application contient un composant COM qu’il envisage de déployer à l’aide de com sans inscription. L’élément contient les attributs suivants.

|Attribut|Description|
|---------------|-----------------|
|`iid`|Obligatoire. ID d’interface (IID) qui est servi par ce proxy. L’IID doit avoir des accolades qui l’entourent.|
|`baseInterface`|facultatif. IID de l’interface à partir de laquelle l’interface référencée par `iid` est dérivée.|
|`numMethods`|facultatif. Nombre de méthodes implémentées par l’interface.|
|`name`|facultatif. Nom de l’interface tel qu’il apparaîtra dans le code.|
|`tlbid`|facultatif. Bibliothèque de types qui contient la description de l’interface spécifiée par l' `iid` attribut.|
|`proxyStubClass32`|facultatif. Mappe un IID à un CLSID dans des dll de proxy 32 bits.|

## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub
 L' `comInterfaceProxyStub` élément est un enfant facultatif de l' `file` élément, mais il peut être nécessaire si l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application contient un composant COM qu’il envisage de déployer à l’aide de com sans inscription. L’élément contient les attributs suivants.

|Attribut|Description|
|---------------|-----------------|
|`iid`|Obligatoire. ID d’interface (IID) qui est servi par ce proxy. L’IID doit avoir des accolades qui l’entourent.|
|`baseInterface`|facultatif. IID de l’interface à partir de laquelle l’interface référencée par `iid` est dérivée.|
|`numMethods`|facultatif. Nombre de méthodes implémentées par l’interface.|
|`Name`|facultatif. Nom de l’interface tel qu’il apparaîtra dans le code.|
|`Tlbid`|facultatif. Bibliothèque de types qui contient la description de l’interface spécifiée par l' `iid` attribut.|
|`proxyStubClass32`|facultatif. Mappe un IID à un CLSID dans des dll de proxy 32 bits.|
|`threadingModel`|facultatif. facultatif. Modèle de thread utilisé par les classes COM in-process. Si cette propriété a la valeur null, aucun modèle de thread n’est utilisé. Le composant est créé sur le thread principal du client et les appels d’autres threads sont marshalés vers ce thread. La liste suivante affiche les valeurs valides :<br /><br /> `Apartment`, `Free`, `Both` et `Neutral`.|

## <a name="windowclass"></a>windowClass
 L' `windowClass` élément est un enfant facultatif de l' `file` élément, mais il peut être nécessaire si l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application contient un composant COM qu’il envisage de déployer à l’aide de com sans inscription. L’élément fait référence à une classe de fenêtre définie par le composant COM qui doit avoir une version appliquée. L’élément contient les attributs suivants.

|Attribut|Description|
|---------------|-----------------|
|`versioned`|facultatif. Contrôle si le nom de classe de fenêtre interne utilisé dans l’inscription contient la version de l’assembly qui contient la classe de fenêtre. La valeur de cet attribut peut être `yes` ou `no` . La valeur par défaut est `yes`. La valeur `no` doit être utilisée uniquement si la même classe de fenêtre est définie par un composant côte à côte et un composant équivalent non côte à côte et que vous souhaitez les traiter comme la même classe de fenêtre. Notez que les règles habituelles relatives à l’inscription de la classe de fenêtre s’appliquent : seul le premier composant qui inscrit la classe de fenêtre sera en mesure de l’inscrire, car aucune version ne lui est appliquée.|

## <a name="hash"></a>Hachage
 L' `hash` élément est un enfant facultatif de l' `file` élément. L’élément `hash` ne comporte pas d’attributs.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utilise un hachage algorithmique de tous les fichiers d’une application en tant que vérification de la sécurité, pour s’assurer qu’aucun des fichiers n’a été modifié après le déploiement. Si l' `hash` élément n’est pas inclus, cette vérification ne sera pas effectuée. Par conséquent, l’omission de l' `hash` élément n’est pas recommandée.

 Si un manifeste contient un fichier qui n’est pas haché, ce manifeste ne peut pas être signé numériquement, car les utilisateurs ne peuvent pas vérifier le contenu d’un fichier non haché.

## <a name="dsigtransforms"></a>dsig:Transforms
 L' `dsig:Transforms` élément est un enfant obligatoire de l' `hash` élément. L’élément `dsig:Transforms` ne comporte pas d’attributs.

## <a name="dsigtransform"></a>dsig:Transform
 L' `dsig:Transform` élément est un enfant obligatoire de l' `dsig:Transforms` élément. L’élément `dsig:Transform` a les attributs suivants.

| Attribut | Description |
|-------------| - |
| `Algorithm` | Algorithme utilisé pour calculer le Digest pour ce fichier. Actuellement, la seule valeur utilisée par [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est `urn:schemas-microsoft-com:HashTransforms.Identity` . |

## <a name="dsigdigestmethod"></a>dsig:DigestMethod
 L' `dsig:DigestMethod` élément est un enfant obligatoire de l' `hash` élément. L’élément `dsig:DigestMethod` a les attributs suivants.

| Attribut | Description |
|-------------| - |
| `Algorithm` | Algorithme utilisé pour calculer le Digest pour ce fichier. Actuellement, la seule valeur utilisée par [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est `http://www.w3.org/2000/09/xmldsig#sha1` . |

## <a name="dsigdigestvalue"></a>dsig:DigestValue
 L' `dsig:DigestValue` élément est un enfant obligatoire de l' `hash` élément. L’élément `dsig:DigestValue` ne comporte pas d’attributs. Sa valeur texte est le hachage calculé pour le fichier spécifié.

## <a name="remarks"></a>Remarques
 Cet élément identifie tous les fichiers qui composent l’assembly qui composent l’application et, en particulier, les valeurs de hachage pour la vérification des fichiers. Cet élément peut également inclure des données d’isolation COM (Component Object Model) associées au fichier. Si un fichier est modifié, le fichier manifeste de l’application doit également être mis à jour pour refléter la modification.

## <a name="example"></a>Exemple
 L’exemple de code suivant illustre les `file` éléments d’un manifeste d’application pour une application déployée à l’aide de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

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
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)