# MFC-Image-Processing

Image reversing

void CImgDlg::OnBnClickedButton1()
{
 int i, j, hig, wid, stride, n;
 hig = img.GetHeight();
 wid = img.GetWidth();
 stride = img.GetPitch();

 BYTE* pBits = (BYTE*)img.GetBits();
 BYTE* pRow;
 n = img.GetBPP() / 8; // How many pixels
 TRACE("bpp=%d", n);
 for (j = 0; j < hig; j++) {
  pRow = pBits + j * stride;
  for (i = 0; i < wid * n; i+=n) {
   pRow[i+0] = 255 - pRow[i+0]; //R
   pRow[i+1] = 255 - pRow[i+1]; //G
   pRow[i+2] = 255 - pRow[i+2]; //B
   // pRow[i+3] = pRow[i+2];  // Transparent
  }
 }
 Invalidate(true);
}
