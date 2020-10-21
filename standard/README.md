The safest way to get the latest revision of an IETF YANG module is to
download the text version of the relevant RFC and then run the `rfcstrip` tool
to extract the YANG. For example:

    wget -O- https://tools.ietf.org/rfc/rfc7223.txt | rfcstrip

This will generate a file for each `CODE BEGINS` ... `CODE ENDS` section in the
RFC. The file names will typically (always?) include the revision date. The
revision date should be retained for old revisions and removed for the current
revision.

This also works for Internet Drafts. For example (note that the version is
omitted so this will always return the latest version):

    wget -O- https://www.ietf.org/id/draft-entitydt-netmod-entity.txt | rfcstrip

An alternative is to assume that [GitHub YangModels/yang](
https://github.com/YangModels/yang/tree/master/standard/ietf/RFC) is up to date
and to fetch any needed files from there. This assumption is not necessarily
valid!

To download the latest revision of `iana-if-type.yang` use the following command:

    wget --no-use-server-timestamps --output-document iana-if-type.yang https://www.iana.org/assignments/iana-if-type-yang/iana-if-type-yang

If this is the only version of the module in this repository, discard the
revision date (if any). Use the revision date only for past versions of
standard modules.
