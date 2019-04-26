---
title: Typedefs de Visual C++ dans le Concepteur de classes
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: ded9e1b6bea0a6f03dd9599b592bba5fba6f91fe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62975120"
---
# <a name="visual-c-typedefs-in-class-designer"></a>Typedefs de Visual C++ dans le Concepteur de classes

Les instructions [Typedef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs) créent une ou plusieurs couches d’indirection entre un nom et son type sous-jacent. Le **Concepteur de classes** prend en charge les types typedef C++ qui sont déclarés avec le mot clé `typedef`, par exemple :

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
} COORD;
```

Vous pouvez ensuite utiliser ce type pour déclarer une instance :

`COORD OriginPoint;`

## <a name="class-and-struct-shapes"></a>Formes de classe et de struct

Dans le **Concepteur de classes**, un typedef C++ a la forme du type spécifié dans le typedef. Si la source déclare `typedef class`, la forme a des angles arrondis et l’étiquette **Class**. Pour `typedef struct`, la forme a des angles carrés et l’étiquette **Struct**.

Les classes et les structures peuvent avoir des typedefs imbriqués déclarés à l’intérieur. Dans le **Concepteur de classes**, les formes de classe et de structure peuvent afficher des déclarations typedef imbriquées comme formes imbriquées.

Les formes typedef prennent en charge les commandes **Afficher en tant qu’association** et **Afficher en tant qu’association de collection** dans le menu contextuel (clic droit).

### <a name="class-typedef-example"></a>Exemple de typedef de classe

```cpp
class B {};
typedef B MyB;
```

![Typedef de classe C++ dans le Concepteur de classes](media/cpp-class-typedef.png)

### <a name="struct-typedef-example"></a>Exemple de typedef de struct

```cpp
typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;
```

![Typedef de struct C++ dans le Concepteur de classes](media/cpp-struct-typedef.png)

## <a name="unnamed-typedefs"></a>Typedefs sans nom

Bien que vous puissiez déclarer un typedef sans nom, le **Concepteur de classes** n’utilise pas le nom de la balise que vous spécifiez. Le **Concepteur de classes** utilise le nom généré par **l’affichage de classes**. Par exemple, la déclaration suivante est valide, mais elle apparaît dans **Affichage de classes** et le **Concepteur de classes** comme objet nommé **__unnamed** :

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

> [!NOTE]
> Le **Concepteur de classes** n’affiche pas les typedefs dont le type source est un pointeur de fonction.

## <a name="see-also"></a>Voir aussi

- [Utiliser le code Visual C++](working-with-visual-cpp-code.md)
- [Typedef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs)