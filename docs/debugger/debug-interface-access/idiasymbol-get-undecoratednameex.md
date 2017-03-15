---
title: "IDiaSymbol::get_undecoratedNameEx | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSymbol::get_undecoratedNameEx (méthode)"
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaSymbol::get_undecoratedNameEx
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait la partie ou la totalité d'un nom non décoré pour le nom décoré par C\+\+ \(liaison\).  
  
## Syntaxe  
  
```cpp#  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### Paramètres  
 `undecoratedOptions`  
 \[in\]  spécifie une combinaison des balises qui contrôlent ce qui est retourné.  Consultez la section Notes pour les valeurs spécifiques et ce qu'ils contiennent.  
  
 `pRetVal`  
 \[out\]  Retourne le nom non décoré pour le nom décoré par C\+\+.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d'erreur.  
  
> [!NOTE]
>  Une valeur de retour d' `S_FALSE` signifie que la propriété n'est pas disponible pour le symbole.  
  
## Notes  
 `undecorateOptions` peut être une combinaison des balises suivantes.  
  
> [!NOTE]
>  Les noms de balises ne sont pas définis dans le diamètre Kit de développement, vous devez ajouter les déclarations à votre code ou utiliser les valeurs brutes.  
  
|Indicateur|Valeur|Description|  
|----------------|------------|-----------------|  
|UNDNAME\_COMPLETE|0x0000|active l'undecoration complet.|  
|UNDNAME\_NO\_LEADING\_UNDERSCORES|0x0001|Supprime des traits de soulignement Microsoft a étendu les mots clés.|  
|UNDNAME\_NO\_MS\_KEYWORDS|0x0002|Désactive l'expansion de étendue Microsoft des mots clés.|  
|UNDNAME\_NO\_FUNCTION\_RETURNS|0x0004|Désactive le développement du type de retour pour la déclaration primaire.|  
|UNDNAME\_NO\_ALLOCATION\_MODEL|0x0008|Désactive le développement du modèle de déclaration.|  
|UNDNAME\_NO\_ALLOCATION\_LANGUAGE|0x0010|Désactive le développement du spécificateur de langage de déclaration.|  
|UNDNAME\_RESERVED1|0x0020|RÉSERVÉ.|  
|UNDNAME\_RESERVED2|0x0040|RÉSERVÉ.|  
|UNDNAME\_NO\_THISTYPE|0x0060|désactive tous les modificateurs sur le type d' `this` .|  
|UNDNAME\_NO\_ACCESS\_SPECIFIERS|0x0080|Désactive l'expansion des spécificateurs d'accès pour les membres.|  
|UNDNAME\_NO\_THROW\_SIGNATURES|0x0100|Désactive l'expansion des « jet\-signatures » des fonctions et des pointeurs fonction.|  
|UNDNAME\_NO\_MEMBER\_TYPE|0x0200|Désactive l'expansion d' `static` ou d' `virtual` .|  
|UNDNAME\_NO\_RETURN\_UDT\_MODEL|0x0400|Désactive le développement du modèle Microsoft de type défini par l'utilisateur.|  
|UNDNAME\_32\_BIT\_DECODE|0x0800|noms décorés 32 bits d'Undecorates.|  
|UNDNAME\_NAME\_ONLY|0x1000|Obtient uniquement le nom de la déclaration principal ; nom de retourne simplement \[portée : :\].  Développe des param de modèle.|  
|UNDNAME\_TYPE\_ONLY|0x2000|L'entrée est simplement un encodage de type ; compose un déclarateur abstrait.|  
|UNDNAME\_HAVE\_PARAMETERS|0x4000|Les véritables paramètres de modèle sont disponibles.|  
|UNDNAME\_NO\_ECSU|0x8000|Supprime l'enum\/class\/struct\/union.|  
|UNDNAME\_NO\_IDENT\_CHAR\_CHECK|0x10000|Supprime le contrôle pour les caractères d'identificateur valides.|  
|UNDNAME\_NO\_PTR64|0x20000|N'inclut pas ptr64 dans la sortie.|  
  
## Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)