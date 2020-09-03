---
title: DisassemblyData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9dcf3316ba57bbb25ee171cba7e4edc4923fa270
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737288"
---
# <a name="disassemblydata"></a>DisassemblyData
Décrit une instruction de désassemblage pour l’environnement de développement intégré (IDE) à afficher.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct tagDisassemblyData {
    DISASSEMBLY_STREAM_FIELDS dwFields;
    BSTR                      bstrAddress;
    BSTR                      bstrAddressOffset;
    BSTR                      bstrCodeBytes;
    BSTR                      bstrOpcode;
    BSTR                      bstrOperands;
    BSTR                      bstrSymbol;
    UINT64                    uCodeLocationId;
    TEXT_POSITION             posBeg;
    TEXT_POSITION             posEnd;
    BSTR                      bstrDocumentUrl;
    DWORD                     dwByteOffset;
    DISASSEMBLY_FLAGS         dwFlags;
} DisassemblyData;
```

```csharp
public struct DisassemblyData { 
    public uint          dwFields;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrCodeBytes;
    public string        bstrOpcode;
    public string        bstrOperands;
    public string        bstrSymbol;
    public ulong         uCodeLocationId;
    public TEXT_POSITION posBeg;
    public TEXT_POSITION posEnd;
    public string        bstrDocumentUrl;
    public uint          dwByteOffset;
    public uint          dwFlags;
};
```

## <a name="members"></a>Membres
`dwFields`\
[DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) constante qui spécifie les champs à remplir.

`bstrAddress`\
L’adresse en tant que décalage à partir d’un point de départ (en général, le début de la fonction associée).

`bstrCodeBytes`\
Octets de code pour cette instruction.

`bstrOpcode`\
Opcode pour cette instruction.

`bstrOperands`\
Opérandes pour cette instruction.

`bstrSymbol`\
Nom du symbole, le cas échéant, associé à l’adresse (symbole public, étiquette, etc.).

`uCodeLocationId`\
Identificateur de l’emplacement du code pour cette ligne désassemblée. Si l’adresse du contexte de code d’une ligne est supérieure à l’adresse du contexte de code d’une autre, l’identificateur de l’emplacement du code désassemblé du premier sera également supérieur à l’identificateur de l’emplacement du code du second.

`posBeg`\
[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) qui correspond à la position dans un document où les données de code machine commencent.

`posEnd`\
[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) qui correspond à la position dans un document où les données de code machine se terminent.

`bstrDocumentUrl`\
Pour les documents texte qui peuvent être représentés en tant que noms de fichiers, le `bstrDocumentUrl` champ est renseigné avec le nom de fichier dans lequel la source peut être trouvée, en utilisant le format `file://file name` .

Pour les documents texte qui ne peuvent pas être représentés en tant que noms de fichiers, `bstrDocumentUrl` est un identificateur unique pour le document et le moteur de débogage doit implémenter la méthode [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) .

Ce champ peut également contenir des informations supplémentaires sur les sommes de contrôle. Pour plus de détails, consultez la section Notes.

`dwByteOffset`\
Nombre d’octets de l’instruction au début de la ligne de code.

`dwFlags`\
[DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) constante qui spécifie les indicateurs actifs.

## <a name="remarks"></a>Notes
Chaque `DisassemblyData` structure décrit une instruction de désassemblage. Un tableau de ces structures est retourné à partir de la méthode [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) .

La structure [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) est utilisée uniquement pour les documents textuels. La plage de codes source pour cette instruction est remplie uniquement pour la première instruction générée à partir d’une instruction ou d’une ligne, par exemple, when `dwByteOffset == 0` .

Pour les documents qui ne sont pas textuels, un contexte de document peut être obtenu à partir du code et le `bstrDocumentUrl` champ doit être une valeur null. Si le `bstrDocumentUrl` champ est le même que le `bstrDocumentUrl` champ de l' `DisassemblyData` élément de tableau précédent, affectez `bstrDocumentUrl` à la valeur null.

Si l' `dwFlags` `DF_DOCUMENT_CHECKSUM` indicateur est défini pour le champ, les informations de somme de contrôle supplémentaires suivent la chaîne pointée par le `bstrDocumentUrl` champ. Plus précisément, après l’indicateur de fin de chaîne NULL, il suit un GUID identifiant l’algorithme de somme de contrôle qui est à son tour suivi d’une valeur de 4 octets qui indique le nombre d’octets dans la somme de contrôle et qui, à son tour, est suivie par les octets de somme de contrôle. Consultez l’exemple de cette rubrique sur la façon d’encoder et de décoder ce champ dans [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] .

## <a name="example"></a>Exemple
Le `bstrDocumentUrl` champ peut contenir des informations supplémentaires autres qu’une chaîne si l' `DF_DOCUMENT_CHECKSUM` indicateur est défini. Le processus de création et de lecture de cette chaîne encodée est simple dans [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] . Toutefois, dans [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] , c’est une autre question. Pour ceux qui sont curieux, l’exemple suivant montre une façon de créer la chaîne encodée à partir de [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] et une façon de décoder la chaîne encodée dans [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] .

```csharp
using System;
using System.Runtime.InteropServices;

namespace MyNamespace
{
    class MyClass
    {
        string EncodeData(string documentString,
                          Guid checksumGuid,
                          byte[] checksumData)
        {
            string returnString = documentString;

            if (checksumGuid == null || checksumData == null)
            {
                // Nothing more to do. Just return the string.
                return returnString;
            }

            returnString += '\0'; // separating null value

            // Add checksum GUID to string.
            byte[] guidDataArray  = checksumGuid.ToByteArray();
            int    guidDataLength = guidDataArray.Length;
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);
            for (int i = 0; i < guidDataLength; i++)
            {
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);
            }
            // Copy guid data bytes to string as wide characters.
            // Assumption: sizeof(char) == 2.
            for (int i = 0; i < guidDataLength / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum count (a 32-bit value).
            Int32 checksumCount = checksumData.Length;
            Marshal.StructureToPtr(checksumCount, pBuffer, true);
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum data.
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);
            for (int i = 0; i < checksumCount; i++)
            {
                Marshal.WriteByte(pBuffer, i, checksumData[i]);
            }
            for (int i = 0; i < checksumCount / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }
            Marshal.FreeCoTaskMem(pBuffer);

            return returnString;
        }

        void DecodeData(    string encodedString,
                        out string documentString,
                        out Guid   checksumGuid,
                        out byte[] checksumData)
        {
            documentString = String.Empty;
            checksumGuid = Guid.Empty;
            checksumData = null;

            IntPtr pBuffer = Marshal.StringToBSTR(encodedString);
            if (null != pBuffer)
            {
                int bufferOffset = 0;

                // Parse string out. String is assumed to be Unicode.
                documentString = Marshal.PtrToStringUni(pBuffer);
                bufferOffset += (documentString.Length + 1) * sizeof(char);

                // Parse Guid out.
                // Read guid bytes from buffer and store in temporary
                // buffer that contains only the guid bytes. Then the
                // Marshal.PtrToStructure() can work properly.
                byte[] guidDataArray  = checksumGuid.ToByteArray();
                int    guidDataLength = guidDataArray.Length;
                IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);
                for (int i = 0; i < guidDataLength; i++)
                {
                    Marshal.WriteByte(pGuidBuffer, i,
                                      Marshal.ReadByte(pBuffer, bufferOffset + i));
                }
                bufferOffset += guidDataLength;
                checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));
                Marshal.FreeCoTaskMem(pGuidBuffer);

                // Parse out the number of checksum data bytes (always 32-bit value).
                int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);
                bufferOffset += sizeof(Int32);

                // Parse out the checksum data.
                checksumData = new byte[dataCount];
                for (int i = 0; i < dataCount; i++)
                {
                    checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Lire](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
