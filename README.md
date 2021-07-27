# Page header
# reclaim-traditional-name-accessibility
## Language
### Language basics
1. [ ] It should be possible to associate a language with any piece of natural language text that will be read by a user.
1. [ ] Where possible, there should  be a way to label natural language changes in inline text.
1. [ ] Consider whether it is useful to express the <a href="https://w3c.github.io/bp-i18n-specdev/#sec_lang_meta">intended linguistic audience</a> of a resource, in addition to specifying the language used for <a href="https://w3c.github.io/bp-i18n-specdev/#sec_text_processing_lang">text processing</a>.
1. [ ] A language declaration that indicates the <a href="https://w3c.github.io/bp-i18n-specdev/#sec_text_processing_lang">text processing language</a> for a range of text must associate  a single language  value with a specific range of text.
1. [ ] Use the HTML <code class="kw" translate="no">lang</code> and XML <code class="kw" translate="no">xml:lang</code> language attributes where appropriate to identify the <a href="https://w3c.github.io/bp-i18n-specdev/#sec_text_processing_lang">text processing language</a>, rather than creating a new attribute or mechanism.
1. [ ] It should be possible to associate a  metadata-type language declaration (which indicates the intended use of the resource rather than the language of a specific range of text)  with multiple language  values.
1. [ ] Attributes that express the language of external resources should not use the HTML <code class="kw" translate="no">lang</code> and XML <code class="kw" translate="no">xml:lang</code> language attributes, but should use a different attribute when they represent metadata (which indicates the intended use of the resource rather than the language of a specific range of text).

### Defining language values
1. [ ] Values for language declarations must use BCP 47.
1. [ ] Refer to BCP 47, not to RFC 5646.
1. [ ] Be specific about what level of conformance you expect for language tags: BCP 47 defines two levels of conformance, "valid" and "well-formed".
1. [ ] Specifications may require implementations to check if language tags are "valid", but in most circumstances should only require that the language tags be "well-formed".
1. [ ] Specifications should require content and content authors to use "valid" language tags.
1. [ ] Reference BCP47 for language tag matching.

### Declaring  language at the resource level
1. [ ] The specification should indicate how to define the default text-processing language for the resource as a whole.
1. [ ] Content within the resource should inherit the language of the text-processing declared at the resource level, unless it is specifically overridden.
1. [ ] Consider whether it is necessary to have separate declarations to indicate the text-processing language versus metadata about the expected use of the resource.
1. [ ] If there is only one language declaration for a resource, and it has more than one language tag as a value, it must be possible to identify the default text-processing language for the resource.

### Establishing the language of a content block
1. [ ] By default, blocks of content should inherit any text-processing language set for the resource as a whole.
1. [ ] It should be possible to indicate a change in language for blocks of content where the language changes.

### Establishing the language of inline runs
1. [ ] It should be possible to indicate language for spans of inline text where the language changes.

## Text direction
### Basic requirements
1. [ ] It must be possible to indicate base direction for each individual paragraph-level item of natural language text that will be read by someone.
1. [ ] It must be possible to indicate base direction changes for embedded runs of inline bidirectional text for all natural language text that will be read by someone.
1. [ ] Annotating right-to-left text must require the minimum amount of effort for people who work natively with right-to-left scripts.

### Background information
1. [ ] Do not assume that direction can be determined from language information.

### Base direction values
1. [ ] Values for the default base direction should include left-to-right, right-to-left, and auto.

### Handling direction in markup
1. [ ] The spec should  indicate how to define a default base direction for the resource as a whole, ie. set the overall base direction.
1. [ ] The  default base direction, in the absence of other information, should be LTR.
1. [ ] The content author must be able to indicate parts of the text where the base direction changes. At the block level, this should be achieved using attributes or metadata, and should not rely on Unicode control characters.
1. [ ] It must be possible to also set the direction for content fragments to <code class="kw" translate="no">auto</code>. This means that the base direction will be determined by examining the content itself.
1. [ ] If the overall base direction is set to <code class="kw" translate="no">auto</code> for plain text, the direction of content paragraphs should be determined on a paragraph by paragraph basis.
1. [ ] To indicate the sides of a block of text  relative to the start and end of its contained lines,  use 'block-start' and 'block-end', rather than 'top' and 'bottom'.
1. [ ] To indicate the start/end of a line  you should use 'start' and 'end', or 'inline-start' and 'inline-end', rather than 'left' and 'right'.
1. [ ] Provide dedicated attributes for control of base direction and bidirectional overrides; do not rely on the user applying style properties to arbitrary markup to achieve bidi control.

### Handling base direction for strings
1. [ ] Provide metadata constructs that can be used to indicate the base direction of any natural language string.
1. [ ] Specify that consumers of strings should use  heuristics, preferably based on the Unicode Standard first-strong algorithm, to detect the base direction of a string except where metadata is provided.
1. [ ] Where possible, define a field to  indicate the default direction for all strings in a given resource or document.
1. [ ] Do NOT assume that a creating a document-level default without the ability to change direction for any string is sufficient.
1. [ ] If metadata is not available due to legacy implementations and cannot otherwise be provided, specifications <em class="rfc2119">MAY<!---0.239331%--></em> allow a base direction to be interpolated from available language metadata.
1. [ ] Specifications <em class="rfc2119">MUST NOT<!---0.239331%--></em> require the production or use of paired bidi controls.

### Setting base direction for inline or substring text
1. [ ] It must be possible to indicate spans of inline text where the base direction changes. If markup is available, this is the preferred method. Otherwise your specification must require that Unicode control characters are recognized by the receiving application, and correctly implemented.
1. [ ] It must be possible to also set the direction for a span to auto. This means that the base direction will be determined by examining the content itself. A typical approach here would be to set the direction based on the first strong directional character outside of any markup.
1. [ ] If users use Unicode bidirectional control characters, the isolating RLI/LRI/FSI with PDI characters must be supported by the application and recommended (rather than RLE/LRE with PDF) by the spec.
1. [ ] Use of RLM/LRM should be appropriate, and expectations of what those controls can and cannot do should be clear in the spec.
1. [ ] For markup, provide dedicated attributes for control of base direction and bidirectional overrides; do not rely on the user applying style properties to arbitrary markup to achieve bidi control.
1. [ ] For markup, allow bidi attributes on all inline elements in markup that contain text.
1. [ ] For markup, provide attributes that allow the user to (a) create an embedded base direction or (b) override the bidirectional algorithm altogether; the attribute should allow the user to set the direction to LTR or RTL or the aforementioned Auto in either of these two scenarios.

## Characters
### Choosing a definition of 'character'
1. [ ] Specifications <em class="rfc2119">SHOULD<!---0.239331%--></em> use specific terms, when available, instead of the general term 'character'.
1. [ ] When specifications use the term 'character' the specifications <em class="rfc2119">MUST<!---0.239331%--></em> define which meaning they intend, and  <em class="rfc2119">SHOULD<!---0.239331%--></em> explicitly define the term 'character' to mean a Unicode code point.
1. [ ] Specifications, software and content <em class="rfc2119">MUST NOT<!---0.239331%--></em> require or depend on a one-to-one relationship between characters and units of physical storage.
1. [ ] Specifications, software and content <em class="rfc2119">MUST NOT<!---0.239331%--></em> require or depend on a one-to-one correspondence between characters and the sounds of a language.
1. [ ] Specifications, software and content <em class="rfc2119">MUST NOT<!---0.239331%--></em> require or depend on a one-to-one mapping between characters and units of displayed text.
1. [ ] Specifications and software <em class="rfc2119">MUST NOT<!---0.239331%--></em> require nor depend on a single keystroke resulting in a single character, nor that a single character be input with a single keystroke (even with modifiers), nor that keyboards are the same all over the world.

### Defining a Reference Processing Model
1. [ ] Textual data objects defined by protocol or format specifications <em class="rfc2119">MUST<!---0.239331%--></em> be in a single character encoding.
1. [ ] All specifications that involve processing of text <em class="rfc2119">MUST<!---0.239331%--></em> specify the processing of text according to the Reference Processing Model described by the rest of the recommendations in this list.
1. [ ] Specifications <em class="rfc2119">MUST<!---0.239331%--></em> define text in terms of Unicode characters, not bytes or glyphs.
1. [ ] For their textual data objects specifications <em class="rfc2119">MAY<!---0.239331%--></em> allow use of any character encoding which can be transcoded to a Unicode encoding form.
1. [ ] Specifications <em class="rfc2119">MAY<!---0.239331%--></em> choose to disallow or deprecate some character encodings and to make others mandatory. Independent of the actual character encoding, the specified behavior <em class="rfc2119">MUST<!---0.239331%--></em> be the same as if the processing happened as follows: (a) The character encoding of any textual data object received by the application implementing the specification <em class="rfc2119">MUST<!---0.239331%--></em> be determined and the data object <em class="rfc2119">MUST<!---0.239331%--></em> be interpreted as a sequence of Unicode characters - this <em class="rfc2119">MUST<!---0.239331%--></em> be equivalent to transcoding the data object to some Unicode encoding form, adjusting any character encoding label if necessary, and receiving it in that Unicode encoding form, (b) All processing <em class="rfc2119">MUST<!---0.239331%--></em> take place on this sequence of Unicode characters, (c) If text is output by the application, the sequence of Unicode characters <em class="rfc2119">MUST<!---0.239331%--></em> be encoded using a character encoding chosen among those allowed by the specification.
1. [ ] If a specification is such that multiple textual data objects are involved (such as an XML document referring to external parsed entities), it <em class="rfc2119">MAY<!---0.239331%--></em> choose to allow these data objects to be in different character encodings. In all cases, the Reference Processing Model <em class="rfc2119">MUST<!---0.239331%--></em> be applied to all textual data objects.

### Including and excluding character ranges 
1. [ ] Specifications <em class="rfc2119">SHOULD NOT<!---0.239331%--></em> arbitrarily exclude code points from the full range of Unicode code points from U+0000 to U+10FFFF inclusive.
1. [ ] Specifications <em class="rfc2119">MUST NOT<!---0.239331%--></em> allow code points above U+10FFFF.
1. [ ] Specifications <em class="rfc2119">SHOULD NOT<!---0.239331%--></em> allow the use of codepoints reserved by Unicode for internal use.
1. [ ] Specifications <em class="rfc2119">MUST NOT<!---0.239331%--></em> allow the use of surrogate code points.
1. [ ] Specifications <em class="rfc2119">SHOULD<!---0.239331%--></em> exclude compatibility characters in the syntactic elements (markup, delimiters, identifiers) of the formats they define.
1. [ ] Specifications <em class="rfc2119">SHOULD<!---0.239331%--></em> allow the full range of Unicode for user-defined values.

### Using the Private Use Area
1. [ ] Specifications <em class="rfc2119">MUST NOT<!---0.239331%--></em> require the use of private use area characters with particular assignments.
1. [ ] Specifications <em class="rfc2119">MUST NOT<!---0.239331%--></em> require the use of mechanisms for defining agreements of private use code points.
1. [ ] Specifications and implementations <em class="rfc2119">SHOULD NOT<!---0.239331%--></em> disallow the use of private use code points by private agreement.
1. [ ] Specifications <em class="rfc2119">MAY<!---0.239331%--></em> define markup to allow the transmission of symbols not in Unicode or to identify specific variants of Unicode characters.
1. [ ] Specifications <em class="rfc2119">SHOULD<!---0.239331%--></em> allow the inclusion of or reference to pictures and graphics where appropriate, to eliminate the need to (mis)use character-oriented mechanisms for pictures or graphics.

### Choosing character encodings
1. [ ] Specifications <em class="rfc2119">MUST<!---0.239331%--></em> either specify a unique character encoding, or provide character encoding identification mechanisms such that the encoding of text can be reliably identified.
1. [ ] When designing a new protocol, format or API, specifications <em class="rfc2119">SHOULD<!---0.239331%--></em> require a unique character encoding.
1. [ ] When basing a protocol, format, or API on a protocol, format, or API that already has rules for character encoding, specifications <em class="rfc2119">SHOULD<!---0.239331%--></em> use rather than change these rules.
1. [ ] When a unique character encoding is required, the character encoding <em class="rfc2119">MUST<!---0.239331%--></em> be UTF-8, or UTF-16.
1. [ ] Specifications <em class="rfc2119">SHOULD<!---0.239331%--></em> avoid using the terms 'character set' and 'charset' to refer to a character encoding, except when the latter is used to refer to the MIME charset parameter or its IANA-registered values. The term 'character encoding', or in specific cases the terms 'character encoding form' or 'character encoding scheme', are <em class="rfc2119">RECOMMENDED<!---0.239331%--></em>.
1. [ ] If the unique encoding approach is not taken, specifications <em class="rfc2119">SHOULD<!---0.239331%--></em> require the use of the IANA charset registry names, and in particular the names identified in the registry as 'MIME preferred names', to designate character encodings in protocols, data formats and APIs.
1. [ ] Character encodings that are not in the IANA registry <em class="rfc2119">SHOULD NOT<!---0.239331%--></em> be used, except by private agreement.
1. [ ] If an unregistered character encoding is used, the convention of using 'x-' at the beginning of the name <em class="rfc2119">MUST<!---0.239331%--></em> be followed.
1. [ ] If the unique encoding approach is not chosen, specifications <em class="rfc2119">MUST<!---0.239331%--></em> designate at least one of the UTF-8 and UTF-16 encoding forms of Unicode as admissible character encodings and <em class="rfc2119">SHOULD<!---0.239331%--></em> choose at least one of UTF-8 or UTF-16 as required encoding forms (encoding forms that <em class="rfc2119">MUST<!---0.239331%--></em> be supported by implementations of the specification).
1. [ ] Specifications that require a default encoding <em class="rfc2119">MUST<!---0.239331%--></em> define either UTF-8 or UTF-16 as the default, or both if they define suitable means of distinguishing them.

### Identifying character encodings
1. [ ] Specifications <em class="rfc2119">MUST NOT<!---0.239331%--></em> propose the use of heuristics to determine the encoding of data.
1. [ ] Specifications <em class="rfc2119">MUST<!---0.239331%--></em> define conflict-resolution mechanisms (e.g. priorities) for cases where there is multiple or conflicting information about character encoding.

### Designing character escapes
1. [ ] Specifications should provide a mechanism for escaping characters, particularly those which are invisible or ambiguous.
1. [ ] Specifications <em class="rfc2119">SHOULD NOT<!---0.239331%--></em> invent a new escaping mechanism if an appropriate one already exists.
1. [ ] The number of different ways to escape a character <em class="rfc2119">SHOULD<!---0.239331%--></em> be minimized (ideally to one).
1. [ ] Escape syntax <em class="rfc2119">SHOULD<!---0.239331%--></em> require either explicit end delimiters or a fixed number of characters in each character escape. Escape syntaxes where the end is determined by any character outside the set of characters admissible in the character escape itself <em class="rfc2119">SHOULD<!---0.239331%--></em> be avoided.
1. [ ] Whenever specifications define character escapes that allow the representation of characters using a number, the number <em class="rfc2119">MUST<!---0.239331%--></em> represent the Unicode code point of the character and <em class="rfc2119">SHOULD<!---0.239331%--></em> be in hexadecimal notation.
1. [ ] Escaped characters <em class="rfc2119">SHOULD<!---0.239331%--></em> be acceptable wherever their unescaped forms are; this does not preclude that syntax-significant characters, when escaped, lose their significance in the syntax. In particular, if a character is acceptable in identifiers and comments, then its escaped form should also be acceptable.

### Storing text
1. [ ] Protocols, data formats and APIs <em class="rfc2119">MUST<!---0.239331%--></em> store, interchange or process text data in logical order.
1. [ ] Independent of whether some implementation uses logical selection or visual selection, characters selected <em class="rfc2119">MUST<!---0.239331%--></em> be kept in logical order in storage.
1. [ ] Specifications of protocols and APIs that involve selection of ranges <em class="rfc2119">SHOULD<!---0.239331%--></em> provide for discontiguous logical selections, at least to the extent necessary to support implementation of visual selection on screen on top of those protocols and APIs.

### Defining 'string'
1. [ ] Specifications <em class="rfc2119">SHOULD NOT<!---0.239331%--></em> define a string as a 'byte string'.
1. [ ] The 'character string' definition <em class="rfc2119">SHOULD<!---0.239331%--></em> be used by most specifications.

### Referring to Unicode characters
1. [ ] Use U+XXXX syntax to represent Unicode code points in the specification.

### Referencing the Unicode Standard
1. [ ] Since specifications in general need both a definition for their characters and the semantics associated with these characters, specifications <em class="rfc2119">SHOULD<!---0.239331%--></em> include a reference to the Unicode Standard, whether or not they include a reference to ISO/IEC 10646.
1. [ ] A generic reference to the Unicode Standard <em class="rfc2119">MUST<!---0.239331%--></em> be made if it is desired that characters allocated after a specification is published are usable with that specification. A specific reference to the Unicode Standard <em class="rfc2119">MAY<!---0.239331%--></em> be included to ensure that functionality depending on a particular version is available and will not change over time.
1. [ ] All generic references to the Unicode Standard <em class="rfc2119">MUST<!---0.239331%--></em> refer to the latest version of the Unicode Standard available at the date of publication of the containing specification.
1. [ ] All generic references to ISO/IEC 10646 <em class="rfc2119">MUST<!---0.239331%--></em> refer to the latest version of ISO/IEC 10646 available at the date of publication of the containing specification.

## Text-processing
### Choosing text units for segmentation, indexing, etc.
1. [ ] The <a class="termref" href="https://www.w3.org/TR/charmod/#def-character-string">character string</a> is <em class="rfc2119">RECOMMENDED<!---0.239331%--></em> as a basis for string indexing.
1. [ ] Grapheme clusters <em class="rfc2119">MAY<!---0.239331%--></em> be used as a basis for string indexing in applications where user interaction is the primary concern.
1. [ ] Specifications that define indexing in terms of grapheme clusters <em class="rfc2119">MUST<!---0.239331%--></em> either: (a) define grapheme clusters in terms of extended grapheme clusters as defined in <a href="https://unicode.org/reports/tr29/">Unicode Standard Annex #29, Unicode Text Segmentation</a> (UTR #29), or (b) define specifically how tailoring is applied to the indexing operation.
1. [ ] The use of <a class="termref" href="https://www.w3.org/TR/charmod/#def-byte-string">byte strings</a> for indexing is <em class="rfc2119">NOT RECOMMENDED<!---0.239331%--></em>.
1. [ ] A UTF-16 <a class="termref" href="https://www.w3.org/TR/charmod/#def-physical-string">code unit string</a> is <em class="rfc2119">NOT RECOMMENDED<!---0.239331%--></em> as a basis for string indexing, even if this results in a significant improvement in the efficiency of internal operations when compared to the use of character string.
1. [ ] Specifications that need a way to identify substrings or point within a string <em class="rfc2119">SHOULD<!---0.239331%--></em> consider ways other than string indexing to perform this operation.
1. [ ] Specifications <em class="rfc2119">SHOULD<!---0.239331%--></em> understand and process single characters as substrings, and treat indices as boundary positions <em>between</em> counting units, regardless of the choice of counting units.
1. [ ] Specifications of APIs <em class="rfc2119">SHOULD NOT<!---0.239331%--></em> specify single characters or single 'units of encoding' as argument or return types.
1. [ ] When the positions between the units are counted for string indexing, starting with an index of 0 for the position at the start of the string is the <em class="rfc2119">RECOMMENDED<!---0.239331%--></em> solution, with the last index then being equal to the number of counting units in the string.

### Matching string identity for identifiers and syntactic content
1. [ ] String identity matching for identifiers and syntactic content should involve the following steps: (a) Ensure the strings to be compared constitute a sequence of Unicode code points (b) Expand all character escapes and includes (c) Perform any appropriate case-folding and Unicode normalization step (d) Perform any additional matching tailoring specific to the specification, and (e) Compare the resulting sequences of code points for identity.
1. [ ] The default recommendation for matching strings in identifiers and syntactic content is to do no normalization (ie. case folding or Unicode Normalization) of content.
1. [ ] <a class="termref" href="https://www.w3.org/TR/charmod-norm/#ASCIIFoldNormalizationStep">'ASCII case fold'</a> and <a href="https://www.w3.org/TR/charmod-norm/#CanonicalFoldNormalizationStep" class="termref">'Unicode canonical case fold'</a> approaches should only be used in special circumstances.
1. [ ] A <a href="https://www.w3.org/TR/charmod-norm/#CompatibilityFoldNormalizationStep" class="termref">'Unicode compatibility case fold'</a> approach should not be used.
1. [ ] Specifications of vocabularies <em class="rfc2119">MUST<!---0.239331%--></em> define the boundaries between syntactic content and character data as well as entity boundaries (if the language has any include mechanism).

### Working with Unicode Normalization
1. [ ] Specifications <em class="rfc2119">SHOULD NOT<!---0.239331%--></em> specify a Unicode normalization form for encoding, storage, or interchange of a given vocabulary.
1. [ ] Implementations <em class="rfc2119">MUST NOT<!---0.239331%--></em> alter the normalization form of syntactic or natural language content being exchanged, read, parsed, or processed except when required to do so as a side-effect of text transformation such as transcoding the content to a Unicode character encoding, case folding, or other user-initiated change, as consumers or the content itself might depend on the de-normalized representation.
1. [ ] Specifications <em class="rfc2119">SHOULD NOT<!---0.239331%--></em> specify compatibility normalization forms (NFKC, NFKD).
1. [ ] Specifications <em class="rfc2119">MUST<!---0.239331%--></em> document or provide a health-warning if canonically equivalent but disjoint Unicode character sequences represent a security issue.
1. [ ] Where operations can produce denormalized output from normalized text input, specifications <em class="rfc2119">MUST<!---0.239331%--></em> define whether the resulting output is required to be normalized or not. Specifications <em class="rfc2119">MAY<!---0.239331%--></em> state that performing normalization is optional for some operations; in this case the default <em class="rfc2119">SHOULD<!---0.239331%--></em> be that normalization is performed, and an explicit option <em class="rfc2119">SHOULD<!---0.239331%--></em> be used to switch normalization off.
1. [ ] Specifications that require normalization <em class="rfc2119">MUST NOT<!---0.239331%--></em> make the implementation of normalization optional.
1. [ ] Normalization-sensitive operations <em class="rfc2119">MUST NOT<!---0.239331%--></em> be performed unless the implementation has first either confirmed through inspection that the text is in normalized form or it has re-normalized the text itself. Private agreements <em class="rfc2119">MAY<!---0.239331%--></em> be created within private systems which are not subject to these rules, but any externally observable results <em class="rfc2119">MUST<!---0.239331%--></em> be the same as if the rules had been obeyed.
1. [ ] A normalizing text-processing component which modifies text and performs normalization-sensitive operations <em class="rfc2119">MUST<!---0.239331%--></em> behave as if normalization took place after each modification, so that any subsequent normalization-sensitive operations always behave as if they were dealing with normalized text.
1. [ ] Specifications that perform comparison or matching of string values <em class="rfc2119">SHOULD<!---0.239331%--></em> specify the appropriate note or warning regarding Unicode normalization.

### Case folding
1. [ ] Specifications and implementations that define string matching as part of the definition of a format, protocol, or formal language (which might include operations such as parsing, matching, tokenizing, etc.) <em class="rfc2119">MUST<!---0.239331%--></em> define the criteria and matching forms used. These <em class="rfc2119">MUST<!---0.239331%--></em> be one of: (a) case-sensitive (b) Unicode case-insensitive using Unicode full case-folding (c) ASCII case-insensitive.
1. [ ] Case-sensitive matching is <em class="rfc2119">RECOMMENDED<!---0.239331%--></em> for matching syntactic content, including user-defined values.
1. [ ] Specifications that define case-insensitive matching in vocabularies that include more than the Basic Latin (ASCII) range of Unicode <em class="rfc2119">MUST<!---0.239331%--></em> specify Unicode full casefold matching.
1. [ ] Specifications that define case-insensitive matching in vocabularies limited to the Basic Latin (ASCII) subset of Unicode <em class="rfc2119">MAY<!---0.239331%--></em> specify ASCII case-insensitive matching.
1. [ ] If language-sensitive case-sensitive matching is specified, Unicode case mappings <em class="rfc2119">SHOULD<!---0.239331%--></em> be tailored according to language and the source of the language used for each tailoring <em class="rfc2119">MUST<!---0.239331%--></em> be specified.
1. [ ] Specifications that define case-insensitive matching in vocabularies <em class="rfc2119">SHOULD NOT<!---0.239331%--></em> specify language-sensitive case-insensitive matching.

### Truncating or limiting the length of strings
1. [ ] Specifications <em class="rfc2119">SHOULD NOT<!---0.239331%--></em> limit the size of data fields unless there is a specific practical or technical limitation.
1. [ ] Specifications that limit the length of a string <em class="rfc2119">MUST<!---0.239331%--></em> specify which type of unit (extended grapheme clusters, Unicode code points, or code units) the length limit uses.
1. [ ] Specifications that limit the length of a string <em class="rfc2119">SHOULD<!---0.239331%--></em> specify the length in terms of Unicode code points.
1. [ ] If a specification sets a length limit in code units (such as bytes), it <em class="rfc2119">MUST<!---0.239331%--></em> specify that truncation can only occur on code point boundaries.
1. [ ] Specifications that limit the length of a string <em class="rfc2119">SHOULD<!---0.239331%--></em> require truncation on grapheme boundaries, as truncation in the midst of a combining or joining sequence can alter the meaning of the string.
1. [ ] If a specification specifies a length limit, it <em class="rfc2119">SHOULD<!---0.239331%--></em> specify that any string that is truncated include an indicator, such as ellipses, that the string has been altered.
1. [ ] When specifying a length limitation in code units (such as bytes), specifications <em class="rfc2119">SHOULD<!---0.239331%--></em> set the maximum length in a way that accommodates users whose language requires multibyte code unit sequences.

### Specifying sort and search functionality
1. [ ] Software that sorts or searches text for users <em class="rfc2119">SHOULD<!---0.239331%--></em> do so on the basis of appropriate collation units and ordering rules for the relevant language and/or application.
1. [ ] Where searching or sorting is done dynamically, particularly in a multilingual environment, the 'relevant language' <em class="rfc2119">SHOULD<!---0.239331%--></em> be determined to be that of the current user, and may thus differ from user to user.
1. [ ] Software that allows users to sort or search text <em class="rfc2119">SHOULD<!---0.239331%--></em> allow the user to select alternative rules for collation units and ordering.
1. [ ] Specifications and implementations of sorting and searching algorithms <em class="rfc2119">SHOULD<!---0.239331%--></em> accommodate text that contains any character in Unicode.

## Resource identifiers
### Basics
1. [ ] Resource identifiers must permit the use of characters outside those of plain ASCII.
1. [ ] Specifications <em class="rfc2119">MUST<!---0.239331%--></em> define when the conversion from IRI references to URI references (or subsets thereof) takes place, in accordance with Internationalized Resource Identifiers (IRIs).

## Markup & syntax
### Defining elements and attributes
1. [ ] Do not define attribute values that will contain user readable content. Use elements for such content.
1. [ ] If you do define attribute values containing user readable content, provide a means to indicate directional and language information for that text separately from the text contained in the element.
1. [ ] Provide a way for authors to annotate arbitrary inline content using a <code class="kw" translate="no">span</code>-like element or construct.

### Defining identifiers
1. [ ] Identifiers should be case-sensitive.

### Working with plain text
1. [ ] Avoid natural language text in elements that only allow for plain text and in attribute values.
1. [ ] Provide a span-like element that can be used for any text content to apply information needed for internationalization.

## Typographic support
### Text decoration
1. [ ] Text decoration such as underline and overline should allow lines to skip ink.
1. [ ] It should be possible to specify the distance of overlines and underlines from the text.

### Vertical text
1. [ ] It should be possible to render text vertically for languages such as Japanese, Chinese, Korean, Mongolian, etc.
1. [ ] Vertical text must support line progression from LTR (eg. Mongolian) and RTL (eg. Japanese).
1. [ ] By default, text decoration, ruby, and the like in vertical text where lines are stacked from left to right (eg. Mongolian) should appear on the same side as for CJK vertical text. Placement should not rely on the <code class="kw" translate="no">before</code> and <code class="kw" translate="no">after</code> line locations.
1. [ ] Vertical writing modes that are equivalent to the <code class="kw" translate="no">vertical-</code> values in CSS (only) should use UTR50 to apply default text orientation of characters. (This does not apply to writing modes that are equivalent to <code class="kw" translate="no">sideways-</code> in CSS.)
1. [ ] By default, glyphs of scripts that are normally horizontal should run along a line in vertical text such that the top of the character is toward the right side of the vertical line, but there should also be a mechanism to allow them to progress down the line in upright orientation. Such a mechanism should use grapheme clusters as a minimum text unit, but where necessary allow syllabic clusters to be treated as a unit when they involve more than one grapheme cluster.
1. [ ] Upright Arabic text in vertical lines should use isolated letter forms and the order of text should read top to bottom.
1. [ ] It should be possible for some sequences of characters (particularly digits) to run horizontally within vertical lines (tate chu yoko).
1. [ ] Writing modes should provide values like <code class="kw" translate="no">sideways-lr</code> and <code class="kw" translate="no">sideways-rl</code> in CSS to allow for vertical rotation of  lines of horizontal script text. UTR50 is not applicable for these cases.

### Cursive text
1. [ ] Overlaps should not be exposed when transparency is applied to the joined letters in cursive text, such as for Arabic, Mongolian, and N'Ko.
1. [ ] When adding a text stroke or shadow, joined letters should not be separated from their neighbors in cursive script text.

### Setting box positioning coordinates when text direction varies
1. [ ] Box positioning coordinates must take into account whether the text is horizontal or vertical.

### Ruby text annotations
1. [ ] 'Ruby' style annotations alongside base text should be supported for Chinese, Japanese, Korean and Mongolian text, in both horizontal and vertical writing modes.
1. [ ] Ruby implementations should  support zhuyin fuhao (bopomofo) ruby for Traditional Chinese.
1. [ ] Ruby implementations should  support a tabular content model (such that ruby contents can be arranged in a sequence approximating to <code class="kw" translate="no">rb rb rt rt</code>).
1. [ ] Ruby implementations should make it possible to use an explicit element for ruby bases, like the <code class="kw" translate="no">rb</code> element in HTML.
1. [ ] Ruby implementations should allow annotations to appear on either or both sides of the base text.

### Miscellaneous
1. [ ] Line heights must allow for characters that are taller than English.
1. [ ] Box sizes must allow for text expansion in translation.
1. [ ] Line wrapping should take into account the special rules needed for non-Latin scripts.
1. [ ] Avoid specifying presentational tags, such as <code class="kw" translate="no">b</code> for bold, and <code class="kw" translate="no">i</code> for italic. 

## Locales, date and time values, and locally affected formats
### Working with locale-affected values
1. [ ] When definining data formats, use locale-neutral serialization forms.

### Working with time
1. [ ] When defining calendar and date systems, be sure to allow for dates prior to the common era, or at least define handling of dates outside the most common range.
1. [ ] When defining time or date data types, ensure that the time zone or relationship to UTC is always defined.
1. [ ] Provide a health warning for conversion of time or date data types that are "floating" to/from incremental types, referring as necessary to the <a href="https://www.w3.org/TR/timezone/"><cite>Time Zones</cite> WG Note</a>.
1. [ ] Allow for leap seconds in date and time data types.
1. [ ] Use consistent terminology when discussing date and time values. Use 'floating' time for time zone independent values.
1. [ ] Keep separate the definition of time zone from time zone offset.
1. [ ] Use IANA time zone IDs to identify time zones. Do not use offsets or LTO as a proxy for time zone.
1. [ ] Use a separate field to identify time zone.
1. [ ] When defining rules for a "week", allow for culturally specific rules to be applied.
1. [ ] When defining rules for week number of year, allow for culturally specific rules to be applied.
1. [ ] When non-Gregorian calendars are permitted, note that the "month" field can go to 13 (undecimber).

### Working with personal names
1. [ ] Check whether you really need to store or access given name and family name separately.
1. [ ] Avoid placing limits on the length of names, or if you do, make allowance for long strings.
1. [ ] Try to avoid using the labels 'first name' and 'last name' in non-localized contexts.
1. [ ] Consider whether it would make sense to have one or more extra fields, in addition to the full name field, where users can provide part(s) of their name that you need to use for a specific purpose.
1. [ ] Allow for users to be asked separately how they would like you be addressed when someone contacts them.
1. [ ] If parts of a person's name are captured separately, ensure that the separate items can capture all relevant information.
1. [ ] Be careful about assumptions built into algorithms that pull out the parts of a name automatically.
1. [ ] Don't assume that a single letter name is an initial.
1. [ ] Don't require that people supply a family name.
1. [ ] ​ Don't forget to allow people to use punctuation such as hyphens, apostrophes, etc. in names.
1. [ ] Don't require names to be entered all in upper case.
1. [ ] Don't normalize the casing in names.
1. [ ] Allow the user to enter a name with spaces.
1. [ ] Don't assume that members of the same family will share the same family name.
1. [ ] It may be better for a form to ask for 'Previous name' rather than 'Maiden name' or 'née'.
1. [ ] You may want to store the name in both Latin and native scripts, in which case you probably need to ask the user to submit their name in both native script and Latin-only form, as separate items.
1. [ ] In standards and standards related documents containing examples that include names of persons, use a variety of names to reflect a global audience. Avoid a bias of names specific to certain regions.

### Designing forms
1. [ ] When defining email field validation, allow for EAI (smtputf8) names.

### Working with numbers
1. [ ] When parsing user input of numeric values, allow for digit shaping (non-ASCII digits).
1. [ ] When formatting numeric values for display, allow for culturally sensitive display, including the use of non-ASCII digits (digit shaping).

### Localization
1. [ ] APIs and protocols <em class="rfc2119">SHOULD<!---0.239331%--></em> provide language independent identifiers for errors.
1. [ ] APIs and protocols <em class="rfc2119">SHOULD<!---0.239331%--></em> include language and base direction metadata for all natural language messages and data fields.
1. [ ] All natural language fields or messages, including error messages, defined by a given API or protocol <em class="rfc2119">SHOULD<!---0.239331%--></em> be localized into the preferred locale of the user or, if that language is not available, supplied with a suitable fallback or default.
1. [ ] Specifications for APIs or protocols <em class="rfc2119">SHOULD<!---0.239331%--></em> define how the user's locale is determined (this is sometimes called <a href="#lang_negotiation">language negotiation</a>).
1. [ ] Specifications <em class="rfc2119">MAY<!---0.239331%--></em> define a specific default language for messages or errors in an API or protocol.

## Navigation
### Providing for  content negotiation based on language
1. [ ] In a multilingual environment it must be possible for the user to receive text in the language they prefer. This may depend on implicit user preferences based on the user's system or browser setup, or on user settings explicitly negotiated with the user.


