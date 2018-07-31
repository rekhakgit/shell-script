#!/bin/bash
MAILHEADER="<h2 style=\"color: #2e6c80;\">Orchestrator server status:</h2>
<table class=\"serverTable\">
<thead>
<tr>
<td>Server</td>
<td>Status</td>
</tr>
</thead>
<tbody>
"
MAILBODY=""
MAILFOOTER="
</tbody>
</table>
<p><strong>&nbsp;</strong></p>
<br/>
<p>Prepared by,</p>
<p>DMT Auditor</p>
<p>For any queries related to this mail reach us at dmt@ericsson.com</p>
"
cat server.txt |  while read output
do
    ping -c 1 "$output" > /dev/null
    if [ $? -eq 0 ]; then
    echo "node $output is up"
    MAILBODY=$MAILBODY "
    <tr>
    <td>" $output "</td>
    <td>RUNNING</td>
    </tr>
    "
    else
    echo "node $output is down"
    MAILBODY=$MAILBODY "
    <tr>
    <td>" $output "</td>
    <td><strong>DOWN</strong></td>
    </tr>
    "
    fi
done

echo $MAILHEADER$MAILBODY$MAILFOOTER
