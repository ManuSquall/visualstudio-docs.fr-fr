---
title: Utilitaire de CreateExpInstance | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bdcb37374c63b96e2169de28c6fe21742024ca98
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="createexpinstance-utility"></a>CreateExpInstance utilitaire
Utilisez l’utilitaire CreateExpInstance pour créer, réinitialiser, ou supprimer une instance expérimentale de Visual Studio. Vous pouvez utiliser l’instance expérimentale pour déboguer et tester des extensions Visual Studio sans modifier le produit sous-jacent.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>Paramètres  
 / Créer  
 Crée l’instance expérimentale.  
  
 / Reset  
 Supprime l’instance expérimentale et crée un nouveau.  
  
 /Clean  
 Supprime l’instance expérimentale.  
  
 / Instancevs  
 Le nom du répertoire qui contient l’instance de Visual Studio de base à copier.  
  
 /Rootsuffix  
 Le suffixe à ajouter au nom du répertoire d’instance expérimentale.  
  
## <a name="remarks"></a>Notes  
 Lorsque vous travaillez sur une extension de Visual Studio, vous pouvez appuyer sur F5 pour ouvrir l’instance expérimentale de valeur par défaut et installer l’extension actuelle. Si aucune instance expérimentale n’est disponible, Visual Studio crée un objet qui contient les paramètres par défaut.  
  
 L’emplacement par défaut de l’instance expérimentale varie selon le numéro de version de Visual Studio. Par exemple, pour Visual Studio 2015, l’emplacement est %localappdata%\Microsoft\VisualStudio\14.0Exp\ tous les fichiers dans l’emplacement du répertoire sont considérés comme faisant partie de cette instance. Toutes les instances expérimentales supplémentaires ne seront pas chargés par Visual Studio, sauf si le nom du répertoire est modifié à l’emplacement par défaut.  
  
 Visual Studio n’accède pas à la base de registres lorsqu’il ouvre l’instance expérimentale. Cela diffère des versions antérieures de Visual Studio, qui ont utilisé une version expérimentale de la ruche du Registre.  
  
 L’utilitaire CreateExpInstance remplace l’utilitaire VsRegEx.  
  
 L’exemple suivant réinitialise l’instance expérimentale de la valeur par défaut de Visual Studio.  
  
 **CreateExpInstance.exe /Reset/vsinstance = 14.0/rootsuffix = Exp**  
  
## <a name="see-also"></a>Voir aussi  
 [VSPackages](../../extensibility/internals/vspackages.md)