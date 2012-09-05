<h3><TMPL_VAR lang_download_file></h3>
<Form name="F1" method="POST" action="" onSubmit="if($$('btn_download').disabled)return false;$$('btn_download').value='<TMPL_IF direct_links><TMPL_VAR lang_generating>...<TMPL_ELSE><TMPL_VAR lang_sending_file>...</TMPL_IF>';$$('btn_download').disabled=true;return true;">
<input type="hidden" name="op" value="download2">
<input type="hidden" name="id" value="<TMPL_VAR file_code>">
<input type="hidden" name="rand" value="<TMPL_VAR rand>">
<input type="hidden" name="referer" value="<TMPL_VAR referer>">

<input type="hidden" name="method_free" value="<TMPL_VAR method_free>">
<input type="hidden" name="method_premium" value="<TMPL_VAR method_premium>">

<div style="display:none;">background:#ccc;text-align <br><b>Password:</b></div>

<table class="file_slot" cellpadding=0 cellspacing=3 width=360>
<tr><td align=right><b><TMPL_VAR lang_file_name>:</b></td><td nowrap><TMPL_VAR file_name><TMPL_IF admin> <a href="<TMPL_VAR site_url>/?op=admin_files&del_code=<TMPL_VAR file_code>" onClick="var x=prompt('<TMPL_VAR lang_delete_file> <TMPL_VAR lang_delete_reason>','');if(typeof(x)=='undefined'||x==null)return false;this.href+='&del_info='+x;"><img src="<TMPL_VAR site_url>/images/del.gif" border=0></a></TMPL_IF></td></tr>
<tr><td align=right><b><TMPL_VAR lang_file_size>:</b></td><td><TMPL_VAR fsize> <small>(<TMPL_VAR file_size> bytes)</small>
&nbsp; <small><a href="<TMPL_VAR site_url>/?op=report_file&amp;id=<TMPL_VAR file_code>"><TMPL_VAR lang_report_abuse></a></small>
</td></tr>
<TMPL_IF file_usr_login><tr><td align=right nowrap><b><TMPL_VAR lang_uploaded_by>:</b></td><td><a href="<TMPL_VAR site_url>/users/<TMPL_VAR file_usr_login>"><TMPL_VAR file_usr_login></a></td></tr></TMPL_IF>
<tr><td width="1%" nowrap align=right><b><TMPL_VAR lang_uploaded_on>:</b></td><td><TMPL_VAR file_created></td></tr>
<tr><td align=right><b><TMPL_VAR lang_downloaded>:</b></td><td><TMPL_VAR file_downloads> <TMPL_VAR lang_times></td></tr>
<TMPL_IF file_descr><tr><td align=right valign=top><b><TMPL_VAR lang_description>:</b></td><td><TMPL_VAR file_descr></td></tr></TMPL_IF>
<TMPL_IF song_url>
<TMPL_IF mp3_artist><tr><td align=right><b>Song Artist:</b></td><td><TMPL_VAR mp3_artist></td></tr></TMPL_IF>
<TMPL_IF mp3_title><tr><td align=right><b>Song Title:</b></td><td><TMPL_VAR mp3_title></td></tr></TMPL_IF>
<TMPL_IF mp3_album><tr><td align=right><b>Song Album:</b></td><td><TMPL_VAR mp3_album> <TMPL_IF mp3_year>(<TMPL_VAR mp3_year>)</TMPL_IF></td></tr></TMPL_IF>

<tr><td align=center colspan=2>
<script type='text/javascript' src='<TMPL_VAR site_url>/player/swfobject.js'></script>
<div id='mp3player'>This text will be replaced</div>
<script type='text/javascript'>
var so = new SWFObject('<TMPL_VAR site_url>/player/player.swf','mpl','420','24','9');
so.addParam('allowfullscreen','true');
so.addParam('allowscriptaccess','always');
so.addParam('wmode','opaque');
so.addVariable('duration','<TMPL_VAR mp3_secs>');
so.addVariable('file','<TMPL_VAR song_url>');
<TMPL_IF mp3_mod_autoplay>so.addVariable('autostart','true');</TMPL_IF>
so.write('mp3player');
</script>
</td></tr>
</TMPL_IF>
<TMPL_IF vid_width>
<TMPL_IF vid_length><tr><td align=right><b>Length:</b></td><td><TMPL_VAR vid_length2></td></tr></TMPL_IF>
<tr><td align=right><b>Video info:</b></td><td><TMPL_VAR vid_codec>,<TMPL_IF vid_bitrate> <TMPL_VAR vid_bitrate> kbps,</TMPL_IF> <TMPL_VAR vid_width>x<TMPL_VAR vid_height>, <TMPL_VAR vid_fps> fps</td></tr>
<tr><td align=right><b>Audio info:</b></td><td><TMPL_VAR vid_audio_codec>
                                               <TMPL_IF vid_audio_bitrate>, <TMPL_VAR vid_audio_bitrate> kbps</TMPL_IF>
                                               <TMPL_IF vid_audio_rate>, <TMPL_VAR vid_audio_rate> Hz</TMPL_IF>
                                           </td></tr>
</TMPL_IF>
<TMPL_IF add_to_account><TD colspan=2 align=right><small id="am<TMPL_VAR file_id>"><a href="#" onClick="return jah('<TMPL_VAR site_url>/?op=my_files&add_my_acc=<TMPL_VAR file_code>','am<TMPL_VAR file_id>');"><TMPL_VAR lang_add_to_my_account></a></small></TD></TMPL_IF>
</table>

<TMPL_IF rar_nfo>
<table class="file_slot" cellpadding=2 cellspacing=1 width=360 style="margin-top:5px;">
<tr class="hdr"><td><TMPL_VAR rar_archive_info></td></tr>
<tr><td>
<TMPL_VAR rar_nfo>
</td></tr>
</table>
</TMPL_IF>


<TMPL_IF image_url>
<br><img src="<TMPL_VAR image_url>" class="pic" alt="<TMPL_VAR file_name>" onLoad="scaleImg(this)" style="-ms-interpolation-mode:bicubic" GALLERYIMG="no">
</TMPL_IF>


<TMPL_IF video_code>
<table cellpadding=0 cellspacing=0 style="margin:auto;margin-top:5px;border:1px solid #555;border-bottom:none;"><tr><td>
<TMPL_IF video_ads>
<TMPL_VAR m_a_css>
<div style="position: relative;">
 <div id="player_img">
    <a href="#" onclick="return player_start();"><img src="<TMPL_VAR site_url>/images/<TMPL_IF divx>player_divx.png<TMPL_ELSE>player_flv.png</TMPL_IF>" style="display:block;width:100%;height:<TMPL_VAR vid_height>px;border:0;"></a>
    <a href="#" onclick="return player_start();" id="vid_play" style="background-image: url(<TMPL_VAR site_url>/images/player_play.png)"></a>
    <div id="player_ads">
      <div style="padding:15px;text-align:center;">
      <!-- Video ADs code start here -->
      <center><table style="background:#f9f9f9;border:3px solid #c3c3c3;width:200px;height:160px;"><tr><td align=center>MY SAMPLE VIDEO ADS</td></tr></table></center>
      <!-- Video ADs code end here -->
      </div>
    </div>
 </div>
</div>
</TMPL_IF>
<div id="player_code"><TMPL_VAR video_code></div>
</td></tr></table>
</TMPL_IF>


<TMPL_IF msg><br><div class="err"><TMPL_VAR msg></div></TMPL_IF>


<TMPL_UNLESS no_link>

<TMPL_IF pass_required><br><b><TMPL_VAR lang_password>:</b> <input type="password" name="password" class="myForm"><br></TMPL_IF>

<TMPL_IF captcha_on>
<br>
<Center>
<TMPL_IF ihtml>
<TMPL_VAR ihtml>
<TMPL_ELSE>
<table><tr><td colspan=2><b><TMPL_VAR lang_enter_code>:</b></td></tr>
<tr><td align=right>
<TMPL_IF iurl><img src="<TMPL_VAR iurl>"></TMPL_IF>
<TMPL_VAR itext>
</td><td align=left valign=middle><input type="text" name="code" class="captcha_code"></td></tr>
</table>
</TMPL_IF>
</Center>
</TMPL_IF>

<TMPL_IF countdown>
<br><span id="countdown_str"><TMPL_VAR lang_wait> <span id="<TMPL_VAR rnd1>"><TMPL_VAR countdown></span> <TMPL_VAR lang_seconds></span>
</TMPL_IF>

<br>

<TMPL_IF direct_links>
<input type="hidden" name="down_direct" value="1">
<input type="submit" id="btn_download" value="Request Download or Streaming Ticket">
<TMPL_ELSE>
<input type="hidden" name="down_script" value="1">
<input type="submit" id="btn_download" value="<TMPL_VAR lang_download_file>">
</TMPL_IF>

</TMPL_UNLESS>

</Form>


<br>
<table cellspacing=0 cellpadding=3 border=0 class="result_slot" width=640><tr><td>
<div class="tabber" style="text-align:left;width:640px;">

<div class="tabbertab">
<h2><TMPL_VAR lang_download_link></h2>
<textarea id="ic0-<TMPL_VAR file_id>" style="width:98%;" cols=24 rows=3 onFocus="copy(this);"><TMPL_VAR download_link></textarea>
</div>

<TMPL_IF thumb_url>
<div class="tabbertab">
<h2><TMPL_VAR lang_forum_code></h2>
<textarea id="ic1-<TMPL_VAR file_id>" style="width:98%;" cols=24 rows=3 onFocus="copy(this);">[URL=<TMPL_VAR download_link>][IMG]<TMPL_VAR thumb_url>[/IMG][/URL]</textarea>
</div>
<div class="tabbertab">
<h2><TMPL_VAR lang_html_code></h2>
<textarea id="ic2-<TMPL_VAR file_id>" style="width:98%;" cols=24 rows=3 onFocus="copy(this);"><a href="<TMPL_VAR download_link>"><img src="<TMPL_VAR thumb_url>" border=0></a></textarea>
</div>
<TMPL_ELSE>
<div class="tabbertab">
<h2><TMPL_VAR lang_forum_link></h2>
<textarea id="ic1-<TMPL_VAR file_id>" style="width:98%;" cols=24 rows=3 onFocus="copy(this);">[URL=<TMPL_VAR download_link>]<TMPL_VAR file_name> - <TMPL_VAR fsize>[/URL]</textarea>
</div>
<div class="tabbertab">
<h2><TMPL_VAR lang_html_code></h2>
<textarea id="ic2-<TMPL_VAR file_id>" style="width:98%;" wrap=hard cols=24 rows=3 onFocus="copy(this);"><a href="<TMPL_VAR download_link>"><TMPL_VAR file_name> - <TMPL_VAR fsize></a></textarea>
</div>
<TMPL_IF video_embed_code>
<div class="tabbertab">
<h2><TMPL_VAR lang_emded_code></h2>
<textarea id="ic4-<TMPL_VAR file_id>" style="width:98%;" cols=24 rows=3 onFocus="copy(this);"><IFRAME SRC="<TMPL_VAR site_url>/embed-<TMPL_VAR file_code>-<TMPL_VAR vid_width>x<TMPL_VAR vid_height>.html" FRAMEBORDER=0 MARGINWIDTH=0 MARGINHEIGHT=0 SCROLLING=NO WIDTH=<TMPL_VAR vid_width> HEIGHT=<TMPL_VAR vid_height2>></IFRAME></textarea>
</div>
<TMPL_IF flv>
<div class="tabbertab">
<h2><TMPL_VAR lang_emded_code>2</h2>
<textarea id="ic5-<TMPL_VAR file_id>" style="width:98%;" cols=24 rows=3 onFocus="copy(this);"><object classid='clsid:D27CDB6E-AE6D-11cf-96B8-444553540000' width='<TMPL_VAR vid_width>' height='<TMPL_VAR vid_height>'>
<param name='movie' value='<TMPL_VAR site_url>/player/player.swf'>
<param name='allowfullscreen' value='true'>
<param name='allowscriptaccess' value='always'>
<param name='wmode' value='transparent'>
<param name='flashvars' value='file=<TMPL_VAR site_url>/vidembed-<TMPL_VAR file_code>.<TMPL_VAR ext>&image=<TMPL_VAR video_img_url>&provider=http'>
<embed src='<TMPL_VAR site_url>/player/player.swf' width='<TMPL_VAR vid_width>' height='<TMPL_VAR vid_height>' bgcolor='#000000' allowscriptaccess='always' allowfullscreen='true' flashvars='file=<TMPL_VAR site_url>/vidembed-<TMPL_VAR file_code>.<TMPL_VAR ext>&image=<TMPL_VAR video_img_url>&provider=http' />
</object></textarea>
</div>
</TMPL_IF>
</TMPL_IF>
<TMPL_IF mp3_embed_code>
<div class="tabbertab">
<h2><TMPL_VAR lang_emded_code></h2>
<textarea id="ic4-<TMPL_VAR file_id>" style="width:98%;" cols=24 rows=3 onFocus="copy(this);"><object classid='clsid:D27CDB6E-AE6D-11cf-96B8-444553540000' width='450' height='24'>
<param name='movie' value='<TMPL_VAR site_url>/player/player.swf'>
<param name='allowfullscreen' value='true'>
<param name='allowscriptaccess' value='always'>
<param name='wmode' value='transparent'>
<param name='flashvars' value='file=<TMPL_VAR site_url>/mp3embed-<TMPL_VAR file_code>.mp3&duration=<TMPL_VAR mp3_secs>'>
<embed src='<TMPL_VAR site_url>/player/player.swf' width='450' height='24' allowscriptaccess='always' allowfullscreen='true' flashvars='file=<TMPL_VAR site_url>/mp3embed-<TMPL_VAR file_code>.mp3&duration=<TMPL_VAR mp3_secs>' />
</object></textarea>
</div>
</TMPL_IF>
</TMPL_IF>

</div>
</td></tr></table>

<div style="position:absolute;display: none;">No such file No such user exist File not found</div>




<Script type="text/javascript" language="JavaScript">
<TMPL_IF countdown>
function countDown()
{
    num = parseInt( $$('<TMPL_VAR rnd1>').innerHTML )-1;
    if(num<=0)
    {
        $$('btn_download').disabled=false;
        $$('countdown_str').style.display='none';
    }
    else
    {
        $$('<TMPL_VAR rnd1>').innerHTML = num;
        setTimeout("countDown()",1000);
    }
}
if($$('btn_download'))
{
    $$('btn_download').disabled=true;
    setTimeout("countDown()",1000);
}
</TMPL_IF>
function checkForm(f1)
{
    if(f1.cmt_name && f1.cmt_name.value==''){alert("<TMPL_VAR lang_name_required>");return false;}
    if(f1.cmt_email && f1.cmt_email.value==''){alert("<TMPL_VAR lang_invalid_email>");return false;}
    if(f1.cmt_text.value.length<5){alert("<TMPL_VAR lang_short_comment>");return false;}
    return true;
}
function copy(obj)
{
  obj.focus();
  obj.select();
}
document.write('<style type="text/css">.tabber{display:none;}<\/style>');
var tab_cookie='tab_down';
</Script>
<script language="JavaScript" type="text/javascript" src="<TMPL_VAR site_url>/tabber.js"></script>

<TMPL_IF enable_file_comments>
<div style="width:500px;text-align:left;margin:10px auto 10px auto;" class="sinput">

<TMPL_INCLUDE comments.html>

</div>
</TMPL_IF>


<TMPL_IF more_files>
<br>
<Table class="tbl1" cellpadding=2 cellspacing=1 width=500>
<TR class="hdr"><TD colspan=2><TMPL_VAR lang_more_from_user></TD></TR>
<TMPL_LOOP more_files>
<TR><TD><a href="<TMPL_VAR download_link>"><TMPL_VAR file_name></a></TD><TD width="1%" nowrap align=right><TMPL_VAR file_size></TD></TR>
</TMPL_LOOP>
</Table>
<br>
</TMPL_IF>

