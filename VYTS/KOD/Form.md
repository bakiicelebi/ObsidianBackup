public Form1()
{
    InitializeComponent();
    form2Instance = new Form2();
    form2Instance.TopLevel = false;
    form2Instance.FormBorderStyle = FormBorderStyle.None;
    form2Instance.Dock = DockStyle.Fill;
    panelSidebar.Controls.Add(form2Instance);
}

private void Form1_Load(obje ct sender, EventArgs e)
{
    panel2.Controls.Clear(); // Eğer varsa paneldeki mevcut içeriği temizle
    panel2.Controls.Add(form2Instance); // Panel içine Form2'yi ekle
    form2Instance.Show();
}

#1F1F1F
#292929
#333333
#525252
#7A7A7A