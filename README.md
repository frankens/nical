nical
=====
using System;
using System.Collections.Generic;
using System.Linq;
using System.Net;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Navigation;
using Microsoft.Phone.Controls;
using Microsoft.Phone.Shell;
using PhoneApp3.Resources;
using Windows.Phone.Speech.Synthesis;

namespace PhoneApp3
{
    public partial class MainPage : PhoneApplicationPage
    {
        SpeechSynthesizer voice;
        public MainPage()
        {
            InitializeComponent();
            this.voice = new SpeechSynthesizer();
        }
        private async void Botton1_Click(object sender, RoutedEventArgs e)
        {
            try
            {
                if (textbox1.Text != "")
                {
                    Button1.IsEnabled = false;
                    await voice.SpeakTextAsync(textbox1.Text);
                    Button1.IsEnabled = true;
                }
                else
                {
                    MessageBox.Show("请输入要读取的内容");
                }
            }
            catch (Exception ex)
            {
                erro.Text = ex.Message;
            }
        }
    }
}
